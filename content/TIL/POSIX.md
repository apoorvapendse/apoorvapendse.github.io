---
tags:
  - unix
  - shell
---
(AI output)
## What is POSIX?

**POSIX** stands for **P**ortable **O**perating **S**ystem **I**nterface.

It is a family of standards created in the 1980s by the IEEE to ensure compatibility across different operating systems. It is much bigger than just the terminal—it dictates how the shell works, how file permissions are structured, how C language APIs behave, and how core command-line utilities (like `grep`, `awk`, `sed`, `ls`) must operate.

- **The Goal:** If you write a shell script or a C program that is "POSIX-compliant," you should be able to drop it onto any Unix-like system (Linux, macOS, BSD, Solaris) and it will run perfectly without any modifications.
    
- **The Downside:** Because it is a global standard that requires consensus among dozens of tech giants, it moves at a glacial pace. It prioritizes rock-solid stability and backward compatibility over fancy new features.