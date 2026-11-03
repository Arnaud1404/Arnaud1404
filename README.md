# Arnaud Gomes

**Français** · [English](https://github.com/Arnaud1404/Arnaud1404/blob/main/README.en.md)

Je suis en deuxième année du master Cryptologie et Sécurité Informatique à l'Université de Bordeaux. Mon terrain, c'est le C et ce qui s'y passe mal. J'exploite à la main, sous débogueur, des corruptions du tas dans l'allocateur de la glibc, et je construis les contrôles d'intégration continue qui devraient attraper le même genre de bogue mémoire bien avant que quelqu'un puisse l'exploiter. Je cherche un stage de fin d'études de six mois en sécurité logicielle ou en recherche de vulnérabilités, à partir de janvier 2027.

Bordeaux · [LinkedIn](https://linkedin.com/in/arnaud-gomes) · [Root Me](https://www.root-me.org/Clippy-1067315) · arnaud.gomes.work@gmail.com

## Projets

### [c-secure-build](https://github.com/Arnaud1404/c-secure-build)

Un petit interpréteur de commandes en C pour Linux, quatre défauts injectés à dessein, et une chaîne qui refuse tout commit tant qu'ils ne sont pas corrigés.

- Flawfinder et Semgrep lisent le code, Valgrind et AddressSanitizer/UBSan le regardent tourner. Toute la chaîne s'exécute dans une image Docker épinglée par digest, avec apt qui lit une archive Ubuntu datée, sous Docker comme sous Podman sans root, pour qu'une autre machine rende le même verdict dans un an.
- Entre les étiquettes `v2-vulnerable` et `v2-patched`, les signalements de sévérité error passent de 4 à 0.
- Un des défauts, une lecture de mémoire non initialisée, échappe aux deux analyseurs statiques comme à AddressSanitizer. Seul Valgrind le voit.
- [`llm-eval/`](https://github.com/Arnaud1404/c-secure-build/tree/main/llm-eval) pose une question simple : un LLM sait-il trier ces signalements entre vrais défauts et faux positifs ? Sur 117 cas [Juliet](https://samate.nist.gov/SARD/test-suites/112) (NIST) étiquetés ligne à ligne, le meilleur modèle local qui tient dans 8 Go de VRAM atteint 85 % d'exactitude équilibrée sous llama.cpp, contre 98 % pour Claude et 66 % pour un Bayes naïf. Il écarte encore 6 vrais défauts sur 50. C'est trop. Le tri reste hors de la chaîne tant qu'un modèle ne peut pas se passer d'un humain qui relit derrière lui.

### [Heap overflows en 2026](https://github.com/Arnaud1404/heap_overflows_2.41)

Travail encadré de recherche, rapport co-écrit à deux.

- Reproduction sous gdb/pwndbg de cinq techniques de [how2heap](https://github.com/shellphish/how2heap) contre l'allocateur de la glibc 2.40 et 2.41 : Fastbin Dup, empoisonnement du tcache, inversion du Safe Linking, chevauchement de chunks et confusion de types.
- Le Safe Linking masque les pointeurs de la liste des blocs libres avec une copie décalée de leur propre adresse. Dès que les douze bits de poids fort d'un pointeur fuient, le masque tombe.
- Datation des contre-mesures qui ferment ces techniques : contrôle de la taille du top chunk en 2.29, retrait de `__malloc_hook` et `__free_hook` en 2.34, suppression des fastbins en 2.43.

## Cours

### Deuxième année de master, en cours

- **Sécurité des systèmes** : analyse statique, rootkits noyau, élévation de privilèges, étude de CVE
- **Sécurité des réseaux** : TLS, certificats X.509, IPsec, Kerberos
- **Cartes à puce** : Java Card, vérification de bytecode, canaux auxiliaires
- **Cryptographie post-quantique** : réseaux euclidiens, LWE, McEliece
- **Vérification des logiciels** : model-checking borné, interprétation abstraite

### Avant

- **Première année de master** : exploitation (ROP, ret2libc, chaînes de format), cryptographie (AES, RSA, Diffie-Hellman), administration réseau (iptables, DNS, LDAP, SSH)
- **Licence d'informatique** : 7e sur 128 en L3

## Compétences

**Langages :** C (C17, POSIX), Python, Bash, assembleur x86-64, SageMath, Java Card (en cours)<br>
**Outils :** gdb/pwndbg, Ghidra, Valgrind, sanitizers, Semgrep, GitHub Actions, Docker, Podman, Wireshark<br>
**Langues :** français (langue maternelle), anglais (C1, Linguaskill Cambridge), vietnamien (A1)

## Projets plus anciens

[LuminaShare](https://github.com/Arnaud1404/LuminaShare), une plateforme de partage d'images en Java. [cuneiform-translator-bot](https://github.com/Arnaud1404/cuneiform-translator-bot), un bot Discord qui renvoie les signes cunéiformes les plus proches d'une chaîne. [Advent of Code 2024](https://github.com/Arnaud1404/AdventOfCode2024) en Python et TypeScript.
