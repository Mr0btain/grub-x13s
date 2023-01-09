# Grub-X13S
Package to fix the bootloader on Lenovo x13s
Something isnt working in grub on the x13s atm so I make a little package to use in 
the meantime.

This will probably be obsolete soon, ive been working on a way to get grub to just work
out of the box and it seems i may have found what the holdup was, testing ATM to be sure

## HEADS UP
I have remove DtbLoader from 1.4.6+. When kernel is built config must include

CONFIG_EFI_ARMSTUB_DTB_LOADER=y
Location in menuconfig:                                                               
  │     -> Device Drivers                                                   
  │       -> Firmware Drivers                                                 
  │         -> EFI (Extensible Firmware Interface) Support                    
  │           -> Enable the DTB loader (EFI_ARMSTUB_DTB_LOADER [=y]) 

And

CONFIG_OF_OVERLAY=y
Location in menuconfig:                                                               
  │     -> Device Drivers                                                     
  │       -> Device Tree and Open Firmware support (OF [=y])                
  │         -> Device Tree overlays (OF_OVERLAY [=y]) 

This allows us to specify specific device trees for each kernel. Including the 
needed modules in grub image we can see all the drives thus not needing dtb loader

## TODO

### Test other OS entries, right now its just for ubuntu being the main OS.
   DONE but needs tested to be sure

### Add a way ti implement per kernel DTBs
   DONE
    
### Add logic to efibootmgr
  Need to add some logic to check if the entry already exists and not make a million
  entrys everytime its run.
    
## DEPS
### Needed to use
    os-prober
    grub-common
    efibootmgr (if you want it to set default bootloader entry, not recommended right 
    now but is a dependancy)
    plymouth-x11
