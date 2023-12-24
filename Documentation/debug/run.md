# Environment

system 6.2.0-39-generic

Library libncurses-dev flex bison libssl-dev libelf-dev build-essential

# Complie

make menconfig

```
Processor type and features  ---> 
    [ ] Build a relocatable kernel                                               
        [ ]  Randomize the address of the kernel image (KASLR) (NEW) 
```

scripts/config --disable SYSTEM_TRUSTED_KEYS

scripts/config --disable SYSTEM_REVOCATION_KEYS

type Enter keyboard

make

# Run

## disk

qemu-img create -f raw disk.raw 512M

mkfs -t ext4 ./disk.raw

## init

### Example


```
/* main.c */
#include <stdio.h>
void main()
{
  printf("Hello World\n");
  fflush(stdout);
  while (1);
}
```

gcc -static -o main main.c
cp main img

### busybox

git clone 

make menuconfig #需要选择编译静态库
make


## commad

qemu-system-x86_64 -m 512M \
                   -kernel arch/x86_64/boot/bzImage  \
                   -drive format=raw,file=./disk.raw  \
                   -append "root=/dev/sda init=/main" \
                   -s -S

gdb 

## Reference

https://www.cnblogs.com/tbolp/p/15219547.html

https://de4dcr0w.github.io/%E5%BF%AB%E9%80%9F%E6%90%AD%E5%BB%BA%E4%B8%80%E4%B8%AALinux%E5%86%85%E6%A0%B8%E8%B0%83%E8%AF%95%E7%8E%AF%E5%A2%83.html


