# Environment

system 6.2.0-39-generic

apt install libncurses-dev flex bison libssl-dev libelf-dev build-essential

# Complie

make menconfig

scripts/config --disable SYSTEM_TRUSTED_KEYS

scripts/config --disable SYSTEM_REVOCATION_KEYS

type Enter keyboard

make

# Run

## disk

qemu-img create -f raw disk.raw 512M

mkfs -t ext4 ./disk.raw

## init

## main

/* main.c */
#include <stdio.h>
void main()
{
  printf("Hello World\n");
  fflush(stdout);
  while (1);
}
gcc -static -o main main.c
cp main img

## busybox

## commad

qemu-system-x86_64 -m 512M \
                   -kernel arch/x86_64/boot/bzImage  \
                   -drive format=raw,file=./disk.raw  \
                   -append "root=/dev/sda init=/main" 

## reference

https://www.cnblogs.com/tbolp/p/15219547.html

