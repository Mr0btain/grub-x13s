# Grub-X13S
Package to fix the bootloader on Lenovo x13s
Something isnt working in grub on the x13s atm so I make a little package to use in 
the meantime.

## TODO

### Test other OS entries, right now its just for ubuntu being the main OS.
  Need to impliment some code to detect if probed OS is in fact the second os
  Right now this is only possible with ubuntu but its a very simple implementation

### Add a way ti implement per kernel DTBs
   Right now it just uses the most recent DTB, but we can pass DTB in linux boot args
   This should be a relatively easy thing to do, prob gonna be in the next iteration
   need to test it and make sure works first
    
### Add logic to efibootmgr
  Need to add some logic to check if the entry already exists and not make a million
  entrys everytime its run.
    
## DEPS
### Needed to use
    grub-common
    efibootmgr (if you want it to set default bootloader entry, not recommended right 
    now but is a dependancy)
