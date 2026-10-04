# Arnaud Gomes

[Français](https://github.com/Arnaud1404) · **English**

I'm a second-year master's student in Cryptology and Computer Security at the University of Bordeaux. I work on C and on what goes wrong in it. Part of that is exploiting heap corruption in the glibc allocator by hand, under a debugger, and the other part is building the CI checks that should catch the same kind of memory bug long before anyone gets to exploit it. I'm looking for a six-month end-of-studies internship in software security or vulnerability research, starting January 2027.

Bordeaux, France · [LinkedIn](https://linkedin.com/in/arnaud-gomes) · [Root Me](https://www.root-me.org/Clippy-1067315) · arnaud.gomes.work@gmail.com

## Projects

### [c-secure-build](https://github.com/Arnaud1404/c-secure-build)

A POSIX shell in C with four planted bugs, and a pipeline that refuses every commit until they are fixed.

- Flawfinder and Semgrep scan the source, Valgrind and AddressSanitizer/UBSan watch it run. The whole gate runs in a Docker image pinned by digest, with apt reading a dated Ubuntu snapshot, under Docker or rootless Podman, so another machine gets the same verdict a year from now.
- Between the `v2-vulnerable` and `v2-patched` tags, error-severity findings drop from 4 to 0.
- One planted bug, a read of uninitialised memory, gets past both static analyzers and AddressSanitizer. Only Valgrind reports it.
- [`llm-eval/`](https://github.com/Arnaud1404/c-secure-build/tree/main/llm-eval) asks whether an LLM can sort those findings into real bugs and false positives. On 117 [Juliet](https://samate.nist.gov/SARD/test-suites/112) (NIST) cases labelled line by line, the best local model that fits in 8 GB of VRAM reaches 85% balanced accuracy under llama.cpp, against 98% for Claude and a 66% naive Bayes floor. It still discards 6 real bugs out of 50. Too many. The triage stays out of the gate until a model can be trusted without a human reading behind it.

### [Heap overflows in 2026](https://github.com/Arnaud1404/heap_overflows_2.41)

Supervised research project, report co-written in French.

- Reproduced five techniques from [how2heap](https://github.com/shellphish/how2heap) against the glibc 2.40 and 2.41 allocator under gdb/pwndbg: Fastbin Dup, tcache poisoning, Safe Linking inversion, overlapping chunks and type confusion.
- Safe Linking masks free-list pointers with a shifted copy of their own address. Once the top twelve bits of a pointer leak, the mask comes off.
- Dated the glibc mitigations that end these techniques: a top chunk size check in 2.29, `__malloc_hook` and `__free_hook` gone in 2.34, fastbins removed in 2.43.

## Coursework

### Second year of the master's, in progress

- **System security:** static analysis, kernel rootkits, privilege escalation, CVE studies
- **Network security:** TLS, X.509 certificates, IPsec, Kerberos
- **Smart cards:** Java Card, bytecode verification, side channels
- **Post-quantum cryptography:** lattices, LWE, McEliece
- **Software verification:** bounded model checking, abstract interpretation

### Before that

- **First year of the master's:** exploitation (ROP, ret2libc, format strings), cryptography (AES, RSA, Diffie-Hellman), network administration (iptables, DNS, LDAP, SSH)
- **Bachelor's in computer science:** ranked 7th of 128 in the final year

## Tools

**Languages:** C (C17, POSIX), Python, Bash, x86-64 assembly, SageMath, Java Card (learning)<br>
**Tooling:** gdb/pwndbg, Ghidra, Valgrind, sanitizers, Semgrep, GitHub Actions, Docker, Podman, Wireshark<br>
**Spoken:** French (native), English (C1, Cambridge Linguaskill), Vietnamese (A1)

## Older projects

[LuminaShare](https://github.com/Arnaud1404/LuminaShare), an image sharing platform in Java. [cuneiform-translator-bot](https://github.com/Arnaud1404/cuneiform-translator-bot), a Discord bot that returns the closest cuneiform signs for a string. [Advent of Code 2024](https://github.com/Arnaud1404/AdventOfCode2024) in Python and TypeScript.
