# `AE` - Arithmetic Expressions

[English](./README.md) | [한국어](./README.ko.md)

Please download the template code as follows:
```bash
sbt new ku-plrg-classroom/ae.g8
```

> :warning: Read the [common instructions](https://github.com/ku-plrg-classroom/docs/blob/main/README.md) first if you have not read them.

The template source code contains the following files:
```
fa-examples
└─ src
   ├─ main/scala/kuplrg
   │  ├── AE.scala ────────────── The definition of the AE and parsers
   │  ├── Implementation.scala ── [[ IMPLEMENT AND SUBMIT THIS FILE ]]
   │  ├── Template.scala ──────── The templates of target functions
   │  └── error.scala ─────────── The definition of the `error` function
   └─ test/scala/kuplrg
      ├─ Spec.scala ───────────── [[ ADD YOUR OWN TESTS ]]
      └─ SpecBase.scala ───────── The base class of test cases
```

The `AE` language is a simple arithmetic expression language that supports
addition and multiplication of integers. In this assignment, you will implement
two functions: `eval` and `countNums`.

## (Problem #1) `eval` (50 points)

The `eval` function evaluates the given expression and returns the result:
```scala
def interp(expr: Expr): Value = ???
```
Please implement the `eval` function in the `Implementation.scala` file.


## (Problem #2) `countNums` (50 points)

The `countNums` function counts the number of `Num` nodes in the given
expression:
```scala
def countNums(expr: Expr): Int = ???
```
Please implement the `countNums` function in the `Implementation.scala` file.


## Definition of `AE`

<details>
<summary markdown="span"><b>See more</b></summary>

### Concrete Syntax

```bnf
<expr>   ::= <number>
           | <expr> "+" <expr>
           | <expr> "*" <expr>
           | "(" <expr> ")"

<digit>  ::= "0" | "1" | ... | "9"
<nat>    ::= <digit> | <digit> <nat>
<number> ::= <nat> | "-" <nat>
```

| Operator | Associativity | Precedence |
|:--------:|:-------------:|:----------:|
| `*`      | Left          | 1          |
| `+`      | Left          | 2          |

### Abstract Syntax

```math
\Large
\begin{array}{lcll}
e
&\texttt{::=}& n & (\texttt{Num}) \\
&\mid& e \; \texttt{+} \; e & (\texttt{Add}) \\
&\mid& e \; \texttt{*} \; e & (\texttt{Mul}) \\
\end{array}
```

### Big-Step Operational Semantics

> :bookmark: The **big-step operational semantics** is also called the **natural
> semantics**.

```math
\Large
\texttt{Num}\frac{
}{
  \vdash n \Rightarrow n
}
\qquad
\texttt{Add}\frac{
  \vdash e_1 \Rightarrow n_1
  \qquad
  \vdash e_2 \Rightarrow n_2
}{
  \vdash e_1 \; \texttt{+} \; e_2 \Rightarrow n_1 + n_2
}
\qquad
\texttt{Mul}\frac{
  \vdash e_1 \Rightarrow n_1
  \qquad
  \vdash e_2 \Rightarrow n_2
}{
  \vdash e_1 \; \texttt{*} \; e_2 \Rightarrow n_1 \times n_2
}
```

</details>