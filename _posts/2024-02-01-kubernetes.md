---
layout: post
title: Setup Kubernetes for my homelab
category: tech
external-url:
---

A few weeks ago, I decided to put my trusty Mac Pro 6,1 (also known as the trash can) to use and create a [Kubernetes](https://kubernetes.io/) cluster as the foundation of my [homelab](https://linuxhandbook.com/homelab/).

Of course, to create a cluster you need multiple machines and some space—something I currently don't have access to. But I won't let this stop me, as we can use virtualization to create all the virtual machines we need. The Mac Pro has a 3.5 GHz 6-Core Intel Xeon E5 (hyperthreaded) and 32 GB of DDR3, which should be more than enough for the computing needs of a small cluster.

 For virtual needs, I always use VMware solutions, so I went ahead and installed the freely available version of [VMware Fusion](https://www.vmware.com/products/fusion.html).

In summary, the idea is to install the OS, Kubernetes, and all the dependencies on a single virtual machine. Then, before initializing the Kubernetes cluster, we can copy this virtual machine to create the worker nodes. Once All the VMs are ready, we will initialize the Kubernetes on the main node and link the worker nodes.

## OS installation
I decided to go with Archlinux. Why? Because I think it's the best distribution around, [`pacman`](https://wiki.archlinux.org/title/pacman) is amazing, the documentation is great, and I have been using it since ~2005. 

Note: I would probably not recommend Archlinux for production due to its rolling-release nature; in a homelab settings, things are allow to break.

The installation process is pretty straightforward following the offical [guide](https://wiki.archlinux.org/title/installation_guide) and using the live system from an [installation medium](https://archlinux.org/download/).

### Some important notes
- Kubernetes does not like `swap`, so make sure it is deactivate (`swapoff -a`) and not present in `/etc/fstab`. More details, in [Archlinux Kubernetes](https://wiki.archlinux.org/title/Kubernetes).
- `dhcpcd.service` is executed by default on the live system, make sure to enable it before rebooting, `systemctl enable dhcpcd.service`.
- Required packages:
```
pacman -S grub vim dhcpcd sudo devtools base-devel
```
some of those require additional configurations. For example, you must add your user to the sudoers group ([sudo](https://wiki.archlinux.org/title/sudo)).

## Networking
I setup bridged networking for the VM settings, so they appear like standalone machines the network from the router point of view. That way it is simple to set up hostname and static ip on the router for all the nodes (e.g. `arch: 192.168.0.200`, `archw1: 192.168.0.201`, `archw2: 192.168.0.202`).

If the machine already has another IP assigned and a DHCP lease, rebooting the router should trigger a renewal.

## Docker
This step is self explanatory:
```
pacman -S docker
usermod -a -G docker phil
systemctl enable docker
systemctl start docker
```

## Kubernetes
I started setting up Kubernetes following this youtube video, [Build a Kubernetes Home Lab from Scratch](https://www.youtube.com/watch?v=_WW16Sp8-Jw) based on Ubuntu. After completing it, I realized that some steps related to networking were missing for Archlinux. I would still recommend to listen to the video once to get an overview of all the steps!

Then, the all steps are summarized in the official [Archlinux Kubernetes](https://wiki.archlinux.org/title/Kubernetes) documentation.

```
pacman -S kubectl kubeadm kubelet containerd
pacman -S ethtool ebtables socat conntrack-tools
systemctl enable kubelet
systemctl start kubelet
```
once installed, complete the configuration steps described in the documentation.

Alright, at this step the VM is ready. We can duplicate it into `n` copies. Remember to login and change the hostname of each machine. It might also be useful to copy your SSH public key (`ssh-copy-id arch`) to avoid having to type the password when login into those VMs.

## Main node
Create the cluster on the main node,
```
kubeadm init
```
then copy the cluster config to the home folder to use `kubectl`.
```
mkdir -p $HOME/.kube
cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
chown $(id -u):$(id -g) $HOME/.kube/config
```
Note: `kubeadm` will output `kubeadm join ...` with the required configuration for worker nodes to join the cluster.

Finally, we have to deploy the pod network. There are difference options, I went with calico without really looking at the pros and cons.
```
kubectl apply -f https://docs.projectcalico.org/manifests/calico.yaml
```

## Worker nodes
For each of the worker nodes, use the `kdeadm join` command that was printed when initializing the cluster on the main node.
```
sudo kubeadm join <k8s>:6443 --token XYZ \
        --discovery-token-ca-cert-hash sha256:XYZ \
        --control-plane --certificate-key XYZ
```

## Cluster
After all this, the cluster should be available and accessible using `kubectl`.
```
$ kubectl get nodes
NAME     STATUS   ROLES           AGE   VERSION
arch     Ready    control-plane   22d   v1.29.3
archw1   Ready    <none>          22d   v1.29.3
archw2   Ready    <none>          22d   v1.29.3
```

## Extras
To start those VMs, I did not want to manually have to click from the VMware dashboard, so I created those two commands that I included in the `~/.zshrc` of the macOS host running the VMs.
```
cluster_start () {
    vmrun start ~/vms/Arch.vmwarevm/Arch.vmx nogui
    vmrun start ~/vms/Arch-w1.vmwarevm/Arch.vmx nogui
    vmrun start ~/vms/Arch-w2.vmwarevm/Arch.vmx nogui
}

cluster_stop () {
    vmrun stop ~/vms/Arch.vmwarevm/Arch.vmx hard
    vmrun stop ~/vms/Arch-w1.vmwarevm/Arch.vmx hard
    vmrun stop ~/vms/Arch-w2.vmwarevm/Arch.vmx hard
}
```

Since, I also interface with another Kubernetes cluster as part of my main gig, I copied the configuration from the main node to `$HOME/.kube/config-lab.yaml` and created this function:
```
homelab () {
	export KUBECONFIG="$HOME/.kube/config-lab.yaml"
}
```
This allow to switch the configuration used by `kubectl` on my laptop and have access to my homelab cluster without having to specify `kubectl --kubeconfig=config-lab.yaml` each time.

## Links
- "Archlinux installation guide" [(link)](https://wiki.archlinux.org/title/Installation_guide)
- "Archlinux Kubernetes" [(link)](https://wiki.archlinux.org/title/Kubernetes)
- "Install and configure Kubernetes on Arch Linux" from Marin Atanasov Nikolov [(link)](http://dnaeon.github.io/install-and-configure-k8s-on-arch-linux/)
- "Build a Kubernetes Home Lab from Scratch" from Brandon Lee [(link)](https://www.youtube.com/watch?v=_WW16Sp8-Jw)