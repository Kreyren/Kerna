# Simplest Boot Sector
These are the bare minimum for BOOT sequence.

```
e9 fd ff 00 00 00 00 00 00 00 00 00 00 00 00 00
00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 29 more lines with sixteen zero-bytes each ]
00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa
```

## Assembly
```nasm
; Infinite loop (e9 fd ff)
loop:
    jmp loop 

; Fill with 510 zeros minus the size of the previous code
times 510-($-$$) db 0
; Magic number
dw 0xaa55 
```
## Requirements
* nasm
* qemu

## To Create
* Copy Assembly code and compile `nasm -f bin boot.asm -o boot.bin`
* To Run `qemu-system-x86_64 boot.bin`
