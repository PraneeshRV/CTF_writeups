

### Question

Something simple to warm you up.


### Approach

We use `file` command to see what type of file is exploit-me. It is a 64 bit, unstripped, ELF file.

Next we can try using `objdump -d exploit-me` to disassemble the functions of the ELF file.

```
0000000000401156 <print_flag>:
  401156:       55                      push   %rbp
  401157:       48 89 e5                mov    %rsp,%rbp
  40115a:       48 8d 05 a3 0e 00 00    lea    0xea3(%rip),%rax        # 402004 <_IO_stdin_used+0x4>
  401161:       48 89 c6                mov    %rax,%rsi
  401164:       48 8d 05 b1 0e 00 00    lea    0xeb1(%rip),%rax        # 40201c <_IO_stdin_used+0x1c>
  40116b:       48 89 c7                mov    %rax,%rdi
  40116e:       b8 00 00 00 00          mov    $0x0,%eax
  401173:       e8 c8 fe ff ff          call   401040 <printf@plt>
  401178:       90                      nop
  401179:       5d                      pop    %rbp
  40117a:       c3                      ret
```

From this, we understand that the function loads 2 addresses `0x402004` and `0x40201c`, so the hardcoded flag might be present in one of them.

We use `radare2` to navigate through the assembly code and print the contents of these memory locations.

After analysing the functions, we can use `x/s 402004` command to rpint the hardcoded flag.

---

### Flag

```
ACECTF{buff3r_0v3rfl3w}