
To install:

```
sudo apt install checksec
```

example:

```
thtad@thtad-HP-240-G8-Notebook-PC:~/Desktop/misc/handlab/build$ checksec --dir=.
RELRO           STACK CANARY      NX            PIE             RPATH      RUNPATH    Symbols      	FORTIFY	Fortified	Fortifiable   Filename
Full RELRO      Canary found      NX enabled    PIE enabled     No RPATH   RUNPATH     44 Symbols	  Yes	2		2		./baseline
Full RELRO      Canary found      NX enabled    PIE enabled     RPATH     No RUNPATH   40 Symbols	  Yes	1		2		./rpath
Full RELRO      Canary found      NX enabled    PIE enabled     No RPATH   RUNPATH     44 Symbols	  No	0		2		./fortify_off
Full RELRO      Canary found      NX enabled    PIE enabled     No RPATH   RUNPATH     40 Symbols	  Yes	1		2		./runpath
Full RELRO      No canary found   NX enabled    PIE enabled     No RPATH   RUNPATH     39 Symbols	  Yes	1		2		./canary_off
Full RELRO      Canary found      NX disabled   PIE enabled     No RPATH   RUNPATH     40 Symbols	  Yes	1		2		./nx_off

```

```
- **RELRO:** relocation sections receive read-only protection; full RELRO also uses immediate binding.
- **Canary:** stack-protector-related symbols were detected.
- **NX:** the stack is marked non-executable according to ELF metadata.
- **PIE:** the executable is position independent and can benefit from ASLR.
- **RPATH/RUNPATH:** embedded library search paths may create loading risks.
- **FORTIFY:** fortified libc calls or related symbols were detected; coverage depends on build conditions.
- **Symbols:** symbols remain available or have been stripped, affecting analysis and sometimes attack surface.
```