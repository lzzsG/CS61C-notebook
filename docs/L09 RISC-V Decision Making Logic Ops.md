---
layout: page
title: L09 RISC-V Decision Making Logic Ops
permalink: /L09
nav_order: 9



---

# Lecture 9: RISC-V Decision Making Logic Ops

# Decision Making

## RV32 So Far...

### RV32 迄今为止...

- **加法/减法**
  - `add rd, rs1, rs2`  
    执行加法操作，将寄存器 `rs1` 和 `rs2` 的值相加，并将结果存储到目标寄存器 `rd` 中。
  - `sub rd, rs1, rs2`  
    执行减法操作，将寄存器 `rs1` 的值减去 `rs2` 的值，并将结果存储到目标寄存器 `rd` 中。

- **加立即数**
  - `addi rd, rs1, imm`  
    执行立即数加法操作，将寄存器 `rs1` 的值与立即数 `imm` 相加，并将结果存储到目标寄存器 `rd` 中。

- **加载/存储**
  - `lw rd, rs1, imm`  
    从地址 `R[rs1] + imm` 加载一个字（32位）到寄存器 `rd` 中。`lw`（Load Word）指令用于从内存中读取数据。
  - `lb rd, rs1, imm`  
    从地址 `R[rs1] + imm` 加载一个字节（8位）到寄存器 `rd` 中。`lb`（Load Byte）指令用于读取单字节数据。
  - `lbu rd, rs1, imm`  
    从地址 `R[rs1] + imm` 加载一个无符号字节（8位）到寄存器 `rd` 中。`lbu`（Load Byte Unsigned）指令会将字节值扩展到寄存器中，而不会考虑符号。
  - `sw rs1, rs2, imm`  
    将寄存器 `rs1` 的值存储到地址 `R[rs2] + imm` 指向的内存位置。`sw`（Store Word）指令用于将数据写入内存。
  - `sb rs1, rs2, imm`  
    将寄存器 `rs1` 的一个字节值存储到地址 `R[rs2] + imm` 指向的内存位置。`sb`（Store Byte）指令用于存储单字节数据。

## Computer Decision Making

### 计算机决策

- **基于计算结果执行不同的操作**  
  计算机可以通过判断计算结果来决定执行不同的操作，这类似于编程语言中的 `if` 语句。
  
- **在编程语言中：`if` 语句**  
  在大多数编程语言中，`if` 语句用于根据条件执行特定的代码块。它的基本语法是：  
  ```c
  if (condition) {
      // Code to execute if condition is true
  }
  ```
  
- **RISC-V：`if` 语句的指令**  
  在RISC-V指令集中，条件分支指令用于根据寄存器的值来改变控制流。例如：
  - `beq reg1, reg2, L1`  
    如果寄存器 `reg1` 的值等于 `reg2`，则跳转到标签 `L1` 指定的位置，执行标记为 `L1` 的指令。  
  - 否则，执行下一条指令。

- **`beq` 表示 "branch if equal"（如果相等则分支）**  
  `beq` 指令用于根据两个寄存器的值是否相等来决定是否跳转到指定标签。  

## Types of Branches

### 分支类型

- **分支**  
  分支指令用于改变程序的控制流，使程序能够根据条件跳转到不同的代码位置。

- **条件分支**  
  条件分支指令根据比较结果改变控制流。常见的条件分支指令包括：
  - `beq`：如果两个寄存器的值相等，则进行分支。
  - `bne`：如果两个寄存器的值不相等，则进行分支。
  - `blt`：如果第一个寄存器的值小于第二个寄存器的值，则进行分支。
  - `bge`：如果第一个寄存器的值大于或等于第二个寄存器的值，则进行分支。
  - **无符号版本**
    - `bltu`：如果第一个寄存器的值小于第二个寄存器的值（按无符号数比较），则进行分支。
    - `bgeu`：如果第一个寄存器的值大于或等于第二个寄存器的值（按无符号数比较），则进行分支。

- **无条件分支**  
  无条件分支指令不依赖于任何条件，始终进行跳转。  
  - RISC-V 指令：`j label`  
    用于跳转到指定的标签 `label`，不考虑任何条件。

## Example if Statement

### 示例 if 语句

假设以下 C 语言代码需要翻译成 RISC-V 指令：

- `f` -> `x10`
- `g` -> `x11`
- `h` -> `x12`
- `i` -> `x13`
- `j` -> `x14`

```c
if (i == j)
  f = g + h;
```

对应的 RISC-V 指令：

- `bne x13, x14, Exit`  
  如果寄存器 `x13` 的值不等于寄存器 `x14` 的值，则跳转到 `Exit` 标签。
- `add x10, x11, x12`  
  如果条件成立，执行加法，将 `x11` 和 `x12` 的值相加，并将结果存储到 `x10`。

`Exit:` 标记结束。此处的 `Exit` 是一个标签，用于指示程序跳转后的继续执行位置。

有时可能需要对分支条件进行取反。此时，可以使用 `bne` 来处理原本使用 `beq` 的条件。

![image-20240731155142682]({{ site.baseurl }}/docs/assets/image-20240731155142682.png)

## Example if-else Statement

### if-else 语句示例

假设以下 C 语言代码需要翻译成 RISC-V 指令：

- `f` -> `x10`
- `g` -> `x11`
- `h` -> `x12`
- `i` -> `x13`
- `j` -> `x14`

```c
if (i == j)
  f = g + h;
else
  f = g - h;
```

对应的 RISC-V 指令：

1. `bne x13, x14, Else`  
   如果寄存器 `x13` 的值不等于寄存器 `x14` 的值，则跳转到 `Else` 标签。
2. `add x10, x11, x12`  
   如果条件成立，执行加法，将 `x11` 和 `x12` 的值相加，并将结果存储到 `x10`。
3. `j Exit`  
   跳转到 `Exit` 标签，跳过 `Else` 部分的执行。
4. `Else: sub x10, x11, x12`  
   如果条件不成立，执行减法，将 `x11` 的值减去 `x12` 的值，并将结果存储到 `x10`。
5. `Exit:`  
   标记结束，程序继续从这里执行。

![image-20240731155211095]({{ site.baseurl }}/docs/assets/image-20240731155211095.png)



## Magnitude Compares in RISC-V

### RISC-V 中的大小比较

在编程中，测试 `<` 和 `>` 操作是非常常见的。RISC-V 提供了多种分支指令来实现这些操作：

- **Branch on Less Than (`blt`)**
  - **语法**：`blt reg1, reg2, Label`
  - **含义**：如果 `reg1 < reg2`，则跳转到 `Label`
  - **示例**：
    ```
    blt x5, x6, TargetLabel  // 如果 x5 小于 x6，则跳转到 TargetLabel
    ```

- **Branch on Less Than Unsigned (`bltu`)**
  - **语法**：`bltu reg1, reg2, Label`
  - **含义**：如果 `reg1 < reg2`（无符号比较），则跳转到 `Label`
  - **示例**：
    ```
    bltu x5, x6, TargetLabel  // 如果 x5 小于 x6（无符号比较），则跳转到 TargetLabel
    ```

此外，还有：

- **Branch on Greater or Equal (`bge`)**
  - **语法**：`bge reg1, reg2, Label`
  - **含义**：如果 `reg1 >= reg2`，则跳转到 `Label`
  - **示例**：
    ```
    bge x5, x6, TargetLabel  // 如果 x5 大于或等于 x6，则跳转到 TargetLabel
    ```

- **Branch on Greater or Equal Unsigned (`bgeu`)**
  - **语法**：`bgeu reg1, reg2, Label`
  - **含义**：如果 `reg1 >= reg2`（无符号比较），则跳转到 `Label`
  - **示例**：
    ```
    bgeu x5, x6, TargetLabel  // 如果 x5 大于或等于 x6（无符号比较），则跳转到 TargetLabel
    ```

注意：RISC-V 中没有 `bgt` 或 `ble` 指令，但可以通过取反相应的比较条件来实现这些操作。

## Loops in C/Assembly

### C/汇编中的循环

C 语言中常见的循环有三种类型：

- **`while` 循环**
  - 语法：`while (condition) { /* 循环体 */ }`
- **`do ... while` 循环**
  - 语法：`do { /* 循环体 */ } while (condition);`
- **`for` 循环**
  - 语法：`for (initialization; condition; increment) { /* 循环体 */ }`

这些循环都可以重写为等效的形式，使用相同的分支指令在 RISC-V 中实现。

关键概念是：在 RISC-V 中，循环的实现依赖于条件分支指令来控制循环的开始和结束。

## C Loop Mapped to RISC-V Assembly

### 将 C 循环映射到 RISC-V 汇编

以下是一个简单的 C 循环及其对应的 RISC-V 汇编实现：

C 代码：

```c
int A[20];
// 填充 A 数据
int sum = 0;
for (int i = 0; i < 20; i++)
  sum += A[i];
```

对应的 RISC-V 汇编指令：

```
add x9, x8, x0    // x9 = &A[0]
add x10, x0, x0   // sum = 0
add x11, x0, x0   // i = 0
addi x13, x0, 20  // x13 = 20

Loop:
  bge x11, x13, Done  // 如果 i >= 20，跳转到 Done
  lw x12, 0(x9)       // x12 = A[i]
  add x10, x10, x12   // sum += x12
  addi x9, x9, 4      // &A[i+1]
  addi x11, x11, 1    // i++
  j Loop              // 跳转到 Loop

Done:
```

![image-20240731155720194]({{ site.baseurl }}/docs/assets/image-20240731155720194.png)

- **初始化**：
  - `add x9, x8, x0`：将数组 `A` 的起始地址存储到寄存器 `x9`。
  - `add x10, x0, x0`：初始化 `sum` 为 0。
  - `add x11, x0, x0`：初始化循环计数器 `i` 为 0。
  - `addi x13, x0, 20`：将常数 20 存储到寄存器 `x13`。

- **循环体**：
  - `bge x11, x13, Done`：如果 `i >= 20`，跳转到 `Done`。
  - `lw x12, 0(x9)`：从 `A[i]` 位置加载数据到 `x12`。
  - `add x10, x10, x12`：将 `A[i]` 的值加到 `sum` 中。
  - `addi x9, x9, 4`：更新 `A` 的指针，指向下一个元素。
  - `addi x11, x11, 1`：递增 `i`。
  - `j Loop`：跳转回循环开始位置。

- **完成**：
  - `Done:` 标签表示循环结束后的执行位置。

## RV32 So Far…

### 到目前为止的 RV32 指令

- **加法/减法**
  - `add rd, rs1, rs2`：将 `rs1` 和 `rs2` 相加，结果存入 `rd`。
  - `sub rd, rs1, rs2`：将 `rs1` 和 `rs2` 相减，结果存入 `rd`。

- **立即数加法**
  - `addi rd, rs1, imm`：将 `rs1` 和立即数 `imm` 相加，结果存入 `rd`。

- **加载/存储**
  - `lw rd, rs1, imm`：从内存地址 `rs1 + imm` 加载字到 `rd`。
  - `lb rd, rs1, imm`：从内存地址 `rs1 + imm` 加载字节到 `rd`。
  - `lbu rd, rs1, imm`：从内存地址 `rs1 + imm` 加载无符号字节到 `rd`。
  - `sw rs1, rs2, imm`：将 `rs1` 存储到内存地址 `rs2 + imm`。
  - `sb rs1, rs2, imm`：将字节 `rs1` 存储到内存地址 `rs2 + imm`。

- **分支**
  - `beq rs1, rs2, Label`：如果 `rs1 == rs2`，跳转到 `Label`。
  - `bne rs1, rs2, Label`：如果 `rs1 != rs2`，跳转到 `Label`。
  - `bge rs1, rs2, Label`：如果 `rs1 >= rs2`，跳转到 `Label`。
  - `blt rs1, rs2, Label`：如果 `rs1 < rs2`，跳转到 `Label`。
  - `bgeu rs1, rs2, Label`：如果 `rs1 >= rs2`（无符号），跳转到 `Label`。
  - `bltu rs1, rs2, Label`：如果 `rs1 < rs2`（无符号），跳转到 `Label`。
  - `j Label`：无条件跳转到 `Label`。

## RISC-V Logical Instructions

### RISC-V 逻辑指令

- **逻辑操作**适用于对字中的位字段进行操作。这些操作对于处理位级别数据非常有用，如对一个字中的字符（8 位）进行操作。

- **位操作指令**
  - `and`：位与操作
  - `or`：位或操作
  - `xor`：位异或操作
  - `sll`：逻辑左移
  - `srl`：逻辑右移

| 逻辑操作       | C 操作符 | Java 操作符 | RISC-V 指令 |
| -------------- | -------- | ----------- | ----------- |
| 按位与 (AND)   | &        | &           | and         |
| 按位或 (OR)    | \|       | \|          | or          |
| 按位异或 (XOR) | ^        | ^           | xor         |
| 逻辑左移       | <<       | <<          | sll         |
| 逻辑右移       | >>       | >>          | srl         |



## RISC-V Logical Instructions

### RISC-V 逻辑指令

RISC-V 提供了多种逻辑指令，用于对位字段进行操作，这些指令包括按位与、按位或、按位异或以及逻辑移位操作。每种指令都有两个变体：寄存器版本和立即数版本。

- **总是有两个变体**
  - 寄存器版本：`and x5, x6, x7`，表示 `x5 = x6 & x7`
  - 立即数版本：`andi x5, x6, 3`，表示 `x5 = x6 & 3`

- **用于“掩码”操作**
  - `andi with 0000 00FF_hex`：隔离最低有效字节
  - `andi with FF00 0000_hex`：隔离最高有效字节

这些指令对于处理位级别的数据非常有用，例如，在图像处理、加密算法等领域。

### 没有逻辑非（NOT）指令

- **没有逻辑 NOT 指令**
  - 使用 `xor` 和 `11111111₂` 实现逻辑非
  - 例如：`xori x5, x6, -1`，将 `x6` 中的所有位取反，并将结果存储在 `x5` 中

| x    | y    | XOR(x, y) |
| ---- | ---- | --------- |
| 0    | 0    | 0         |
| 0    | 1    | 1         |
| 1    | 0    | 1         |
| 1    | 1    | 0         |

在 RISC-V 中，逻辑 NOT 操作可以通过对值进行 XOR 操作并与全 1 进行 XOR 实现。这是由于 RISC-V 追求简洁性，没有直接提供 NOT 指令。

## Logical Shifting

### 逻辑移位

RISC-V 提供了逻辑左移和逻辑右移指令，用于将寄存器中的位向左或向右移动，并在空位中插入零。

- **逻辑左移（sll）和立即数逻辑左移（slli）**

  - `slli x11, x12, 2`：将 `x12` 中的值左移 2 位，结果存储到 `x11` 中
  - 在 C 语言中等效于 `<<`
  - 例如：
    - 移位前：`0000 0002ₕ = 0000 0000 0000 0000 0000 0000 0000 0010₂`
    - 移位后：`0000 0008ₕ = 0000 0000 0000 0000 0000 0000 0000 1000₂`

  左移操作在寄存器中将值向左移动，并在右边插入 0。这样的操作在计算机中用于乘法等操作。

- **逻辑右移（srl）**

  - 逻辑右移的操作与左移相反，在左边插入 0，向右移动位。

## Arithmetic Shifting

### 算术移位

RISC-V 提供了算术右移指令，用于将寄存器中的值向右移动，并在空位中插入符号位，从而保持符号。

- **算术右移（sra, srai）**

  - `sra` 和 `srai` 将 n 位向右移动，并在空位中插入高位符号位。
  - 例如，如果寄存器 `x10` 包含 `1111 1111 1111 1111 1111 1111 1110 0111₂ = -25₁₀`
  - 执行 `srai x10, x10, 4` 后结果是：`1111 1111 1111 1111 1111 1111 1111 1110₂ = -2₁₀`

  算术右移与除以 2 的 n 次方不同，尤其对于奇数负数，这种操作可能不符合期望的结果。在 C 语言中，算术语义要求除法结果向 0 舍入。

## Assembler to Machine Code (More Later in Course)

### 汇编器到机器代码（课程后面会详细讲解）

汇编器的作用是将人类可读的汇编代码转换为指令的位模式，从而生成机器代码目标文件。以下是一个汇编器和链接器的工作流程：

- 汇编源文件（.S 文件）
- 汇编器将其转换为机器代码目标文件（.o 文件）
- 链接器将多个目标文件和预构建的目标文件库（lib.o）链接成一个可执行的机器代码文件（a.out）

![image-20240731160506346]({{ site.baseurl }}/docs/assets/image-20240731160506346.png)

## How Program is Stored

### 程序的存储方式

程序在内存中存储为字节：

- 程序代码
- 数据

一个 RISC-V 指令占用 32 位（4 字节）。

![image-20240731160556472]({{ site.baseurl }}/docs/assets/image-20240731160556472.png)

## Program Execution

### 程序执行

程序计数器（PC）是处理器内部的一个寄存器，它保存下一个要执行的指令的字节地址。执行过程如下：

1. 从内存中获取指令。
2. 控制单元使用数据路径和内存系统执行指令，并更新程序计数器。
3. 默认情况下，PC 加 4 字节以移动到下一个顺序指令；分支和跳转指令会改变这个默认行为。

![image-20240731160629405]({{ site.baseurl }}/docs/assets/image-20240731160629405.png)

## Helpful RISC-V Assembler Features

### 有用的 RISC-V 汇编器功能

- **符号寄存器名称**
  - 例如，a0-a7 用于函数调用的参数寄存器（x10-x17）。
  - 例如，zero 代表 x0 寄存器。

- **伪指令**
  - 常见汇编惯用语法的简写。
  - 例如，`mv rd, rs = addi rd, rs, 0`（移动指令）。
  - 例如，`li rd, 13 = addi rd, x0, 13`（加载立即数）。
  - 例如，`nop = addi x0, x0, 0`（空操作）。

## Example: Translate \*x = \*y

### 示例：将 \*x = \*y 翻译为 RISC-V 指令

我们要将 \*x = \*y 翻译成 RISC-V 指令，x 和 y 的指针分别存储在 x3 和 x5 寄存器中。以下是逐步指令翻译：

1. `lw x6, 0(x5)`：从 x5 指向的内存地址加载值到 x6。
2. `sw x6, 0(x3)`：将 x6 中的值存储到 x3 指向的内存地址。

这些指令将实现从 y 指针指向的内存地址加载值并存储到 x 指针指向的内存地址。

## Your Turn. What is in x12?

### x12 中的值是多少？

假设 x10 存储了 0x34FF，以下是指令的执行步骤：

1. `slli x12, x10, 0x10`：将 x10 左移 16 位，结果为 0x34FF0000。
2. `srli x12, x12, 0x08`：将 x12 右移 8 位，结果为 0x0034FF00。
3. `and x12, x12, x10`：将 x12 和 x10 按位与，结果为 0x00003400。

最终，x12 中的值是 0x00003400。