###
```bash

sudo dnf install -y qemu-kvm libvirt-daemon-kvm virt-install virt-manager libvirt-devel

sudo systemctl enable --now libvirtd
sudo usermod -aG libvirt $(whoami)
newgrp libvirt
```

### Install vagrant
```bash
vagrant --version
vagrant plugin install vagrant-libvirt
vagrant plugin list
vagrant global-status
```

### Install molecule
```bash
sudo dnf install python3-pip
python3 -m pip install --user molecule
python3 -m pip install --user "molecule-plugins[podman]" "molecule-plugins[vagrant]"
```

###
https://github.com/ansible-community/molecule-plugins/tree/main/doc/vagrant
```bash
molecule init scenario vagrant

molecule --debug destroy --scenario-name vagrant
molecule reset --scenario-name vagrant

molecule test --scenario-name default --report --command-borders
molecule test --scenario-name vagrant --report --command-borders
molecule list
```

###
```bash
sudo virsh list --all
sudo virsh vol-list --pool default
sudo virsh vol-delete molecule._rAf.vagrant_stream10.img --pool default
```

###
```bash
cd ~/.ansible/tmp/molecule._rAf.vagrant
vagrant destroy -f
vagrant destroy up
```