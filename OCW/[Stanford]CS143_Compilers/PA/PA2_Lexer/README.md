# PA01 Lexical Analysis

## Summary

1. Learn how to use `flex/jlex` to match legal tokens. For example, `2143abd` is illegal in C.
2. Report error information when error occurs.

## Related Files

- **grading**: After judging, the folder will be created. The folder contains 63 test cases.
- **pa1-grading.pl**: The grading shell script.
- **cool.flex**: What we need to code.
- **cool-parse.h**: The definition of token types to return.
- **stringtab.h**: Where to save the token's value.
- **Makefile**: Use `$ make lexer` to compile.


## Instructions

1. [Getting started with the VMs](https://class.stanford.edu/courses/Engineering/Compilers/Fall2014/9f961242edfb45eba0969a5a7592916d/) (ID:**compilers**, PW:**cool**)
2. Assignment number begins from `2`, ex: assignment I is `PA2`.
3. Create the directory you want to do hw, ex: `~/cool/my_assign_sol/PA2`
4. Copy source into the working directory.
  - C++: `PA2 $ make -f /usr/class/cs143/assignments/PA2/Makefile`
  - Java: `PA2 $ make -f /usr/class/cs143/assignments/PA2J/Makefile`
5. Start to code.

## Sample I/O

**Run**

- `./lexer sample.cool`

<details>
<summary>Input: [grading/stringcomment.cool](grading/stringcomment.cool)</summary>

```
"This is a string--and it's still a string"
--This is a comment, "not a string"
(* "not a string" *)
"(* not a comment *)"
```

</details>

<details>
<summary>Output: [grading/stringcomment.cool.out](grading/stringcomment.cool.out)</summary>

```
#name "stringcomment.cool"
#1 STR_CONST "This is a string--and it's still a string"
#4 STR_CONST "(* not a comment *)"
```

</details>

## Commands

- **Compile**: `$ make lexer`
- **Execute**: `$ ./lexer good.cl`
- **Judge**
  1. Download the script: `$ wget http://spark-university.s3.amazonaws.com/stanford-compilers/scripts/pa1-grading.pl`
  2. Setting the Permission: `$ chmod a+x pa1-grading.pl`
	3. Submit: `$ perl pa1-grading.pl`

## References

- [Assignment 1 Spec](https://s3-us-west-1.amazonaws.com/prod-edx/Compilers/ProgrammingAssignments/PA1.pdf)
- [The Cool Reference Manual](https://lagunita.stanford.edu/c4x/Engineering/Compilers/asset/cool_manual.pdf), Sec. 10 and Figure 1
- [A Tour of the Cool Support Code](https://lagunita.stanford.edu/c4x/Engineering/Compilers/asset/cool-tour.pdf), Sec. 3 "String Tables"
- [Lex - A Lexical Analyzer Generator](http://dinosaur.compilertools.net/lex/index.html)

## Tips

- **To answer to ambiguous cases, you can read the test cases carefully.**
- Use `$ find ~ -name "cool-parse.h"` to find the file **cool-parse.h**.
- How do I ssh into my VM?
  1. Set the network setting of VM to use NAT.
  2. Close the VM.
  3. In the host OS, create the port forwording rule in the Terminal.
    - `$ VBoxManage modifyvm myserver --natpf1 "ssh,tcp,,3022,,22"`
  4. Ensure the Rule is created.
    - `$ VBoxManage showvminfo myserver | grep 'Rule'`
  5. Start the VM
  6. Install Openssh-Server: `$ sudo apt-get install openssh-server`
  7. ssh into the VM: `$ ssh -p 3022 compilers@127.0.0.1`