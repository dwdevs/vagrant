# This is a deployment of mac-os Sequoia (Currently not working)

Vagrant & VirtualBox

Read the attached PDF for install instructions

Manual VBox VM deploy:

```bash
VBoxManage createvm --name "mac-sequoia" --register

VBoxManage modifyvm "mac-sequoia" --memory 4096 --cpus 2 --nic1 nat

VBoxManage createhd --filename "~/VirtualBox VMs/mac-sequoia/mac-sequoia.vdi" --size 20480

VBoxManage storagectl "mac-sequoia" --name "SATA Controller" --add sata --controller IntelAHCI

VBoxManage storageattach "mac-sequoia" --storagectl "SATA Controller" --port 0 --device 0 --type hdd --medium "~/VirtualBox VMs/mac-sequoia/mac-sequoia.vdi"

VBoxManage storageattach "mac-sequoia" --storagectl "SATA Controller" --port 1 --device 0 --type dvddrive --medium "/Users/don/Desktop/Sequoia.iso"
```
