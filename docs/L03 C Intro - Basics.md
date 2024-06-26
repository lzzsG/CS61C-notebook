---
layout: page
title: L03 C Intro - Basics
permalink: /L03
nav_order: 3


---



# C 简介 - 基础知识

---

本节是 CS 61C L03 C Intro - Basics

首先探讨了如何利用硬件的底层特性，通过编程语言C来实现更接近硅片（silicon）的操作。C语言因其能够直接管理内存而受到推崇，尽管这在Java或Python中是不常见的。此外，本讲座也涉及了特殊的硬件指令，如并行化指令，以及C语言的流行度和其历史演变。

## C语言的特性与风险
C语言让程序员可以直接与硬件对话，并进行内存管理，这是其核心特性之一。然而，这也带来了许多安全风险，因为C语言中的指针和数组等可以导致程序错误，这些错误可能不会立即导致程序崩溃，而是让程序处于不一致或可被利用的状态。

## 现代编程语言的选择
尽管C语言在功能强大，但在开始一个全新的项目时，可能会选择其他语言如Rust和Go，这两种语言都具有C语言的特性但进行了优化。Rust提供了安全性改进，避免了C语言中常见的错误；Go语言则自动管理多核处理，简化了并行计算的复杂性。

## 编程实践与学习方法
这部分强调了编程技能必须通过实践来学习，仅仅通过听讲座是不够的。因此，设置实验室和编程练习是必要的。此外，讲座还提供了一些从Java转向C的学习资源，帮助学生理解两种语言的不同之处。

## 编译与解释
这部分讨论了编译语言和解释语言的区别，强调了C语言是一种完全编译型语言，这与Python和Java的解释执行方式形成对比。讲座解释了为什么某些情况下选择编译型语言，主要是为了性能优化。

## 编译过程的深入理解
这部分介绍了编译、汇编和链接的步骤（简称CAL），这是生成可执行程序的关键过程。这些步骤虽然在使用GCC等工具时被隐藏，但了解它们对于理解程序是如何构建的至关重要。

## 文件协作与编译过程

在这段内容中，描述了一个团队协作的编程场景，其中两个程序员分别独立工作在不同的C文件上（例如food.c和bar.c）。每个程序员都有自己的编译器，最终产生机器代码文件（.o文件）。这种方法允许每个成员在不影响其他人的情况下独立工作，同时编译结果可以通过链接库等方式组合成一个完整的可执行文件（.out文件）。此外，讲述了使用GCC的-o标志来为输出文件命名的重要性，避免使用默认的a.out文件名，这被认为是新手的表现。

![image-20240503212633211]({{ site.baseurl }}/docs/assets/image-20240503212633211.png)

## 优化编译时间与Make文件的作用

这部分讲解了通过适当的文件管理和使用Make文件来优化编译过程的方法。Make文件可以识别不同文件间的依赖关系，当某个文件被修改时，只重新编译依赖该文件的部分，而不是整个项目。这样做不仅减少了等待编译的时间，也提高了开发效率。例如，如果只修改了food.c文件，而bar.c文件没有变动，那么在编译时只需重新编译food.c相关的部分。

## 运行性能与编程语言的选择

讨论了为何在需要高运行性能的场景下，编译语言通常比解释语言更有优势。编译语言如C可以直接编译成针对特定硬件优化的机器代码，从而提供更高的执行效率。同时，也提到了Python在数据科学和大规模数据处理（如使用Spark）中的应用优势，因为它可以方便地调用分布式计算资源，并且能够通过Cython等工具调用C语言编写的底层库，这样结合了Python的易用性和C的性能优势。

## 架构特定性和代码移植性

这一部分主要讨论了编译语言（如C语言）的架构特定性，即编译出的代码只能在特定的硬件架构上运行。当库或架构发生变化时，通常需要重新编译代码，这是因为不同的硬件架构可能需要不同的编译设置和库配置。这种架构依赖性导致了代码的移植性问题，即将代码从一种架构迁移到另一种架构是一个复杂且非琐碎的过程，尤其是在进行底层系统编程时。为了应对这些挑战，开发者需要使用如makefiles和configure等工具来适配不同的环境和配置。

## 开发周期和并行编译

讲解了传统的“修改-编译-运行”开发循环，这个循环对于那些喜欢快速迭代和立即看到结果的开发者来说可能显得缓慢和烦人。为了优化这一过程，提到了使用并行编译的方法，即通过make工具并行处理多个独立的编译任务，从而加速整体的编译过程。然而，链接阶段仍然需要顺序执行，这常常成为编译过程中的瓶颈。

## C预处理器的作用

最后，介绍了C预处理器（CPP）的功能，它是编译过程中的一个预处理步骤。预处理器允许开发者在C代码中使用预处理指令（如#define和#include），这些指令在编译之前对源代码进行必要的修改和配置。例如，使用预处理指令可以根据不同的硬件架构条件编译代码，或者自动包含必要的头文件。这使得C代码可以在不同的环境中更加灵活和可移植，尽管根本上C语言是架构依赖的。

![image-20240503212704542]({{ site.baseurl }}/docs/assets/image-20240503212704542.png)

## 宏的使用和副作用

宏在C语言中是一种基于文本替换的功能，常用于定义简单的函数，如最小值函数（min）。由于宏是直接替换文本，而非函数调用，因此它们可以带来一些非预期的副作用。例如，如果宏中包含有副作用的操作（如输出），在宏展开时这些副作用会重复发生。这种特性需要开发者在使用宏时格外小心，确保不会因为文本替换导致逻辑错误或重复执行副作用操作。

## C语言与Java语言的比较

这部分内容对C语言和Java语言进行了比较。Java是一种面向对象的编程语言，强调封装和对象的管理，而C语言则是以函数为中心的，更注重具体函数的操作而不是对象。这两种语言在内存管理上有本质的差异：Java具有自动垃圾收集机制，可以自动管理内存，而C语言需要程序员显式地使用malloc和free等函数来管理内存。这种差异使得Java在编写代码时可能更为简便，但C语言在性能和底层操作上提供了更大的灵活性和控制力。

![image-20240503212744860]({{ site.baseurl }}/docs/assets/image-20240503212744860.png)

![image-20240503212807408]({{ site.baseurl }}/docs/assets/image-20240503212807408.png)

![image-20240503212830130]({{ site.baseurl }}/docs/assets/image-20240503212830130.png)

## C语言的注释与常量定义

### 注释的嵌套问题
C语言中使用`/* */`进行多行注释，但存在一个问题是不支持注释的嵌套。如果尝试嵌套注释，会导致编译错误，因为编译器无法正确解析结束标记。相比之下，Java语言支持`//`进行单行注释，这样的方式较为灵活且不会引起嵌套问题。

### 常量的定义方式
在C语言中，可以通过`#define`预处理命令或`const`关键字定义常量，而在Java中使用`final`关键字。这些常量的定义有助于保证变量值不被修改，增强代码的安全性和可读性。

## 变量声明与运算符

### 变量的声明位置
C语言要求变量在代码块的开始处声明，而Java允许在使用前任何位置声明，这使得Java在变量声明方面较为灵活。

### 运算符的使用
C语言和 Java 在运算符方面非常相似，包括算术运算符、位运算符、逻辑运算符等。这表明两种语言在表达式的构建上具有高度的一致性。

## C语言的更新与改进

### C99标准
1999年的C99标准引入了多项改进，如在`for`循环中声明变量、单行注释的支持、可变长度数组等，这些都是从Java中借鉴过来的特性。这些改进使得C语言在使用上更加灵活和强大。

### C11和C18标准
后续的C11和C18标准进一步增加了多线程支持、Unicode支持和类型通用宏等现代编程需求，提高了C语言在多核处理和国际化应用中的能力。这些更新显示了C语言不断适应现代计算需求的努力。

C语言虽然是一种较老的编程语言，但通过不断的更新和改进，它仍然保持着与现代编程需求相符合的能力。与Java的比较显示了两种语言各有优势，但都在不断进化中寻求改善和优化。

## C语言主函数和命令行参数

### 主函数结构
在C语言中，`main`函数是每个程序的入口点。它通常包含两个参数：`int argc`和`char *argv[]`。`argc`表示命令行参数的数量，包括程序名本身；`argv`是一个指向字符串数组的指针，这些字符串代表传递给程序的各个参数。这种结构允许程序接收和处理来自命令行的输入。

### 命令行参数的应用
`argv[0]`存储的是程序的名称，这在生成使用说明（usage strings）时特别有用。当需要显示如何正确调用程序时，可以利用`argv[0]`来动态显示程序名，这对于处理程序名称变更或在不同环境中调用程序时保持指令的准确性非常重要。

## 真值和假值的概念

### C语言中的真假值
在C语言中，`0`和`NULL`（空指针）被视为假（false），而所有其他值则被视为真（true）。这与其他语言（如Scheme）中的布尔处理略有不同，其中只有特定的符号（例如`#f`）表示假。C语言的这种处理方式简洁且直观，使得条件判断更为直接。

## 变量类型和声明

### 不变的类型声明
在C语言中，一旦变量被声明为某种类型，它就保持那种类型直到作用域结束。这与Java等语言相似，强类型的特性有助于避免类型错误和提高代码的可靠性。

### 整数和浮点数
C语言提供了多种数值类型，包括整数（`int`）、无符号整数（`unsigned int`）、浮点数（`float`）、双精度浮点数（`double`）、字符（`char`）、以及更大范围的整数类型（`long`和`long long`）。每种类型都有其特定的用途和存储需求，例如`int`和`unsigned int`用于存储整数，`float`和`double`用于存储小数。

![image-20240503213002534]({{ site.baseurl }}/docs/assets/image-20240503213002534.png)

### 类型的存储大小
C语言中，不同的整数类型（如`int`、`long`、`long long`）有不同的存储大小，这取决于编译器和运行平台。这一点在跨平台编程时需要特别注意，因为类型的大小变化可能会影响程序的行为和数据处理。

![image-20240503213059594]({{ site.baseurl }}/docs/assets/image-20240503213059594.png)

## 常量和枚举的使用

### 常量的定义
在C语言中，常量可以通过`#define`预处理指令或`const`关键字定义，用于锁定变量值，防止其在程序运行过程中被修改。例如，定义速度光速或一周天数等常量值，这些值在程序中不应被更改。

### 枚举类型
枚举（enum）是C语言中用于定义一组命名的整数常量的数据类型。枚举提高了代码的可读性和可维护性。例如，定义一个交通灯颜色的枚举包括红色、绿色和蓝色。使用枚举可以避免使用魔法数字（magic numbers），即代码中硬编码的数字，这样可以更清晰地表达代码的意图。

![image-20240503213134725]({{ site.baseurl }}/docs/assets/image-20240503213134725.png)

## 函数类型和抽象数据类型

### 函数的类型声明
C语言要求明确声明函数的返回类型。这包括普通数据类型（如`int`、`float`等）和`void`类型，后者表示函数不返回任何值。函数的参数类型也必须声明，这有助于编译器检查类型安全性，防止类型错误。

### 类型安全的重要性
类型安全是C语言中的一个重要概念，有助于在编译时捕捉到可能的错误。例如，如果函数声明返回`float`类型，但错误地尝试将其作为`int`类型处理，则编译器可以警告程序员。这种类型检查对于初学者尤其有益，因为它可以防止常见的编程错误。

### 结构体和抽象数据类型
结构体（struct）是C语言中用于创建复合数据类型的关键工具。通过结构体，可以将多个相关的数据项组合成一个单独的数据结构。例如，可以定义一个表示歌曲的结构体，其中包含歌曲的长度和发布年份。结构体支持更复杂的数据模型和高级的数据抽象，尽管它不具备面向对象编程语言中的封装和继承特性。

![image-20240503213221397]({{ site.baseurl }}/docs/assets/image-20240503213221397.png)

C语言提供了强大的语法和结构来支持高级编程需求，如数据抽象、类型安全和模块化设计。通过枚举、常量定义、函数类型声明和结构体等特性，C语言允许开发者编写清晰、可维护和效率高的低级代码。虽然这些特性增加了语言的复杂性，但也提供了更大的控制力和灵活性，使得C语言成为系统编程和性能敏感型应用的首选语言。

## 控制流与错误处理

### 控制流结构
C语言中的控制流结构如`if-else`、`while`、`do-while`、`for`循环和`switch`语句与Java非常相似，因为Java的设计受到了C语言的强烈影响。在C语言中使用花括号来定义控制结构的范围是一个常见的做法，尽管在语法上不是必需的，但它可以防止因为缺少花括号而产生的逻辑错误。

![image-20240503213319587]({{ site.baseurl }}/docs/assets/image-20240503213319587.png)

![image-20240503213344092]({{ site.baseurl }}/docs/assets/image-20240503213344092.png)

### `goto`语句的使用
C语言支持`goto`语句，它可以无条件地跳转到程序中的另一个点。然而，`goto`通常被视为**不良编程实践**，因为它可以导致代码结构混乱和难以追踪的错误。在实际编程中应尽量避免使用`goto`，除非绝对必要。

## C语言程序示例

### 程序结构和变量声明
在示例的C程序中，使用`#include`引入数学库，主函数中声明了多个变量，如角度和对应的弧度值。通过`printf`函数输出数据，展示了如何在C中进行基础的输入输出操作。这显示了C语言在处理数学计算和格式化输出方面的能力。

### 变量初始化
C语言要求在使用变量之前进行初始化，否则变量可能包含垃圾值。这与Java不同，Java会自动将未初始化的变量设置为默认值。C语言中的这一特点增加了编程的复杂性，但也给程序员提供了更大的控制力。

![image-20240503213414565]({{ site.baseurl }}/docs/assets/image-20240503213414565.png)

这段C程序的主要功能是计算并打印从0度到360度的正弦值（Sine values）。代码分析如下：

```c
#include <stdio.h>
#include <math.h>

int main(void)
{
    int angle_degree; // 定义角度变量（以度为单位）
    double angle_radian, pi, value; // 定义弧度变量、π值和正弦值变量

    printf("Compute a table of the sine function\n\n"); // 打印程序功能描述
    pi = 4.0 * atan(1.0); // 计算π的值，atan(1.0)返回π/4
    printf("Value of PI = %f\n\n", pi); // 显示计算得到的π值
    printf("Angle\tSine\n"); // 打印表头

    angle_degree = 0; // 初始化角度为0
    while (angle_degree <= 360) { // 循环从0度到360度
        angle_radian = pi * angle_degree / 180.0; // 将角度转换为弧度
        value = sin(angle_radian); // 计算当前弧度的正弦值
        printf("%3d\t%f\n", angle_degree, value); // 打印当前角度和对应的正弦值
        angle_degree += 10; // 角度增加10度，准备下一次循环
    }

    return 0; // 程序结束
}
```

### 程序解释：

1. **头文件包含**：
   - `<stdio.h>`：用于输入输出函数如`printf`。
   - `<math.h>`：包含数学函数如`sin`和`atan`。

2. **变量声明**：
   - `angle_degree`：整型变量，用于存储角度，以度为单位。
   - `angle_radian`：浮点型变量，存储将角度转换为弧度后的值。
   - `pi`：浮点型变量，存储π的值。
   - `value`：浮点型变量，存储计算出的正弦值。

3. **计算π值**：使用`4.0 * atan(1.0)`计算π的值。因为`atan(1.0)`返回的是π/4，所以乘以4得到π。

4. **输出表头**：打印"Angle"和"Sine"，准备输出正弦值表。

5. **循环计算正弦值**：
   - 使用`while`循环从0度循环到360度。
   - 在每次循环中，首先将角度从度转换为弧度（角度*π/180）。
   - 使用`sin`函数计算出弧度的正弦值。
   - 使用`printf`打印当前的角度和对应的正弦值。
   - 角度每次增加10度。

这个程序是一个简单的使用C语言进行数学计算和输出的示例，显示了如何使用循环结构和数学函数来生成一个正弦值表。

## 错误类型与调试

### 未初始化的变量和未定义行为
C语言中未初始化的变量可能导致未定义的行为，这是C编程中常见的错误源。这种行为可能导致程序输出不可预测的结果，增加了调试和维护的难度。

### Bug类型
C语言中的错误（bug）可以分为两类：常规错误（bore bugs）和难以复现的错误（heisenbugs），后者类似于量子力学中的海森堡不确定性原理，指出在观察某些系统时无法同时准确知道所有的物理属性。

## 结论
C语言提供了与Java相似但更底层的控制流构造，允许程序员以更接近硬件的方式来操作数据和处理逻辑。然而，C语言也带来了更高的复杂性和潜在的错误风险，尤其是在处理未初始化的变量和未定义行为时。通过正确使用控制结构和严格管理变量的生命周期，可以在C语言中编写高效且可靠的代码。