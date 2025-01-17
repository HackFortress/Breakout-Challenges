1. connect to the gdbserver instance. Within gdb execute `target remote localhost:8080`. 
2. Execute `disassemble main` to see the contents of main. Take a moment to understand what's going on here.
3. Breaking at the call function and printing the `rsi` register shows the flag.

```
(remote) gef➤  disassemble
Dump of assembler code for function main:
   0x0000580de9e0064a <+0>:     push   rbp
   0x0000580de9e0064b <+1>:     mov    rbp,rsp
   0x0000580de9e0064e <+4>:     sub    rsp,0x20
   0x0000580de9e00652 <+8>:     mov    DWORD PTR [rbp-0x14],edi
   0x0000580de9e00655 <+11>:    mov    QWORD PTR [rbp-0x20],rsi
   0x0000580de9e00659 <+15>:    lea    rax,[rip+0xb8]        # 0x580de9e00718
   0x0000580de9e00660 <+22>:    mov    QWORD PTR [rbp-0x8],rax
   0x0000580de9e00664 <+26>:    mov    rax,QWORD PTR [rbp-0x8]
   0x0000580de9e00668 <+30>:    mov    rsi,rax
   0x0000580de9e0066b <+33>:    lea    rdi,[rip+0xcc]        # 0x580de9e0073e
   0x0000580de9e00672 <+40>:    mov    eax,0x0
=> 0x0000580de9e00677 <+45>:    call   0x580de9e00520 <printf@plt>
   0x0000580de9e0067c <+50>:    mov    eax,0x0
   0x0000580de9e00681 <+55>:    leave
   0x0000580de9e00682 <+56>:    ret
End of assembler dump.
(remote) gef➤  x/s $rsi
0x580de9e00718: "flag{attacking_exposed_ports_is_1337}"
(remote) gef➤
```
