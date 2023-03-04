## kernel-rdtsc-patch
*slightly scripted* and updated version of [WCharacter/RDTSC-KVM-Handler](https://github.com/WCharacter/RDTSC-KVM-Handler)

## Usage
```
curl -O https://raw.githubusercontent.com/lexi-src/kernel-rdtsc-patch/master/patch.sh
chmod +x patch.sh
./patch.sh
```

## Tick manipulation
Intel CPUs:

* nano -l +6004 **arch/x86/kvm/vmx/vmx.c**
* u64 fake_diff =  diff / ***16***; <<< The bold int is the value you divide by.

AMD CPUs:

* nano -l +3151 **arch/x86/kvm/svm/svm.c**
* u64 fake_diff =  diff / ***20***; <<< The bold int is the value you divide by.

## Kernel Compile / Installation
You'll need to follow your distros compiling guide.

## After installation
enable qemu:commandline in your libvirt xml then add:

```
<qemu:arg value="-cpu"/>
<qemu:arg value="host,rdtscp=off,-hypervisor"/>
```
