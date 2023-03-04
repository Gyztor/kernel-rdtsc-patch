## kernel-rdtsc-patch
*slightly scripted* and updated version of [WCharacter/RDTSC-KVM-Handler](https://github.com/WCharacter/RDTSC-KVM-Handler)

## Usage
```
curl -O https://raw.githubusercontent.com/lexi-src/kernel-rdtsc-patch/master/patch.sh
chmod +x patch.sh
./patch.sh
```

## Tick manipulation
For Intel users:

* Open vmx.c in text editor
* Find handle_rdtsc function
* Change **u64 fake_diff =  diff / 16;**
* 16 is a divider of actual difference in timestamp, you can increase and decrease it

For AMD users:

* Open svm.c in text editor
* Find handle_rdtsc_interception function
* Change **u64 fake_diff =  diff / 20;**
* 20 is a divider of actual difference in timestamp, you can increase and decrease it 

## Kernel Compile / Installation
You'll need to follow your distros compiling guide.

## After installation
enable qemu:commandline in your libvirt xml

```
<qemu:arg value="-cpu"/>
<qemu:arg value="host,rdtscp=off,-hypervisor"/>
```
