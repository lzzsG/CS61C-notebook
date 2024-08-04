---
layout: post
title: CS 61C
nav_order: 0
description: "YourHomeDescription"
permalink: /
---

# 开始

<br/>

今天开始我们一起学习 CS 61C。

CS 61C 是加州大学伯克利分校（UC Berkeley）提供的一门课程，全称为“Great Ideas in Computer Architecture”（计算机体系结构中的伟大思想），通常也被称为“Machine Structures”（机器结构）。这门课程主要关注于计算机硬件和软件的接口，强调理解计算机是如何工作的，尤其是从底层硅芯片到高层编程语言的整个流程。

### 主要教学内容

1. **计算机体系结构的基本概念**：包括数据路径、控制、流水线、缓存、虚拟内存和存储系统等。
2. **硬件与软件的交互**：深入探讨编程语言如C语言是如何与硬件直接交互的，以及这种交互对性能的影响。
3. **并行计算**：介绍并行计算的不同形式，包括指令级并行（ILP）、数据级并行（DLP）和线程级并行（TLP）。
4. **实用项目和实验**：通过实际的CPU设计、逻辑门等硬件组件的教学，帮助学生理解理论知识如何在实际中应用。

### 教学方法和课程设计

- **互动和实践**：CS 61C 强调通过实践和项目来学习，课程设计包括大量的实验室和项目作业，鼓励学生通过实际操作来深化对课程材料的理解。
- **理论与实践的结合**：课程旨在帮助学生理解理论知识与实际应用之间的桥梁，如何将理论应用于解决实际问题。
- **资源丰富**：除了面授课程，伯克利大学还提供了丰富的在线资源和录制的课程讲座，便于学生复习和自学。

CS 61C 不仅是一门深入探讨计算机硬件的课程，也是介绍软件开发和系统设计基本概念的课程。通过这门课程，学生可以获得坚实的计算机系统结构基础，为更高级的计算机科学课程和职业生涯做好准备。

更多关于这门课程的信息可以通过加州大学伯克利分校的官方网站查询，或者通过各种教育平台访问相关课程内容和资源。

我们的学习使用的是[CS 61C Fall 2022](https://inst.eecs.berkeley.edu/~cs61c/fa22/)版本，在B站有对应的[视频](https://www.bilibili.com/video/BV1s7421T7XR)。



---

该翻译补充笔记由 LzzsG 基于 [CS 61C](https://cs61c.org) / Garcia, Yan 的作品创作，采用的是 [CC BY-NC-SA 许可](https://creativecommons.org/licenses/by-nc-sa/4.0/)。

<br/>

<br/>

| Part | 标题                                                         | 中文                                               |
| :--: | ------------------------------------------------------------ | -------------------------------------------------- |
|  P1  | Lecture 1: Intro                                             | 讲座1：介绍                                        |
|  P2  | Lecture 2: Number Representation                             | 讲座2：数字表示                                    |
|  P3  | Lecture 3: C Intro - Basics                                  | 讲座3：C 介绍 - 基础                               |
|  P4  | Discussion 1: Number Representation                          | 讨论1：数字表示                                    |
|  P5  | Lecture 4: C Intro - Pointers, Arrays, Strings               | 讲座4：C 介绍 - 指针，数组，字符串                 |
|  P6  | Lecture 5: Memory(Mis)Management                             | 讲座5：内存（误）管理                              |
|  P7  | Discussion 2: C                                              | 讨论2：C                                           |
|  P8  | Lecture 6: Floating Point                                    | 讲座6：浮点数                                      |
|  P9  | Lecture 7: Intro to Assembly Language RISC-V                 | 讲座7：RISC-V 汇编语言介绍                         |
| P10  | Lecture 8: RISC-V DataTransfer                               | 讲座8：RISC-V 数据传输                             |
| P11  | Discussion 3: Floating Point                                 | 讨论3：浮点数                                      |
| P12  | Lecture 9: RISC-V Decision Making Logic Ops                  | 讲座9：RISC-V 决策逻辑操作                         |
| P13  | Lecture 10: RISC-V Procedures                                | 讲座10：RISC-V 程序                                |
| P14  | Lecture 11: RISC-V Instruction Formats I                     | 讲座11：RISC-V 指令格式I                           |
| P15  | Discussion 4: RISC-V Intro, Control Flow                     | 讨论4：RISC-V 介绍，控制流                         |
| P16  | Lecture 12: RISC-V Instruction Formats II                    | 讲座12：RISC-V 指令格式II                          |
| P17  | Lecture 13: Compiler, Assembler, Linker, Loader              | 讲座13：编译器，汇编器，链接器，加载器             |
| P18  | Lecture 14: Intro to Synchronous Digital Systems             | 讲座14：同步数字系统介绍                           |
| P19  | Discussion 5: RISC-V Procedures, ISA, CALL                   | 讨论5：RISC-V 程序，ISA，CALL                      |
| P20  | Lecture 15: Combinational Logic                              | 讲座15：组合逻辑                                   |
| P21  | Lecture 16: SDS State, FSMs                                  | 讲座16：SDS 状态，有限状态机                       |
| P22  | Lecture 17: Combinational Logic Blocks                       | 讲座17：组合逻辑模块                               |
| P23  | Discussion 6: SDS, Logic FSM                                 | 讨论6：SDS，逻辑有限状态机                         |
| P24  | Lecture 18: RISC-V Single Cycle Datapath I                   | 讲座18：RISC-V 单周期数据通路I                     |
| P25  | Lecture 19: RISC-V Single Cycle Datapath II                  | 讲座19：RISC-V 单周期数据通路II                    |
| P26  | Lecture 20: RISC-V Single-Cycle Control                      | 讲座20：RISC-V 单周期控制                          |
| P27  | Discussion 7: Single-Cycle Datapath                          | 讨论7：单周期数据通路                              |
| P28  | Lecture 21: RISC-V 5-Stage Pipeline I                        | 讲座21：RISC-V 五级流水线I                         |
| P29  | Lecture 22: RISC-V 5-Stage Pipeline II, Hazards              | 讲座22：RISC-V 五级流水线II，冒险                  |
| P30  | Lecture 23: RISC-V 5-Stage Pipeline III, Hazards             | 讲座23：RISC-V 五级流水线III，冒险                 |
| P31  | Discussion 8: Pipelining, Hazards                            | 讨论8：流水线，冒险                                |
| P32  | Lecture 24: Caches - Direct Mapped I                         | 讲座24：缓存 - 直接映射I                           |
| P33  | Lecture 25: Caches - Direct Mapped II                        | 讲座25：缓存 - 直接映射II                          |
| P34  | Lecture 26: Caches - MultiLevel                              | 讲座26：缓存 - 多级                                |
| P35  | Discussion 9: Caches                                         | 讨论9：缓存                                        |
| P36  | Lecture 27: Caches - Set-Associative, Performance with Caches | 讲座27：缓存 - 组关联，缓存性能                    |
| P37  | Lecture 28: Flynn Taxonomy, SIMD                             | 讲座28：Flynn 分类法，SIMD                         |
| P38  | Lecture 29: Parallelism I: Thread-level Parallelism          | 讲座29：并行I：线程级并行                          |
| P39  | Discussion 10: Multi-Level Caches, AMAT                      | 讨论10：多级缓存，AMAT                             |
| P40  | Lecture 30: Parallelism II: OpenMP, Sharing Issues           | 讲座30：并行II：OpenMP，共享问题                   |
| P41  | Lecture 31: Parallelism III: Cache Coherence, Performance    | 讲座31：并行III：缓存一致性，性能                  |
| P42  | Lecture 32: VM I: Intro                                      | 讲座32：虚拟机I：介绍                              |
| P43  | Discussion 11: Parallelism, Coherency, and Atomic            | 讨论11：并行性，一致性，和原子性                   |
| P44  | Lecture 33: VM II: Page Faults, Multilevel, Interrupts/Exceptions | 讲座33：虚拟机II：页面错误，多级，中断/异常        |
| P45  | Lecture 34: VM III: TLB                                      | 讲座34：虚拟机III：TLB                             |
| P46  | Lecture 35: VM Performance, I/O                              | 讲座35：虚拟机性能，输入输出                       |
| P47  | Lecture 36: MapReduce, Spark, Amdahl's Law, Data-level Parallelism | 讲座36：MapReduce，Spark，阿姆达尔定律，数据级并行 |
| P48  | Lecture 37: Dependability, Parity, ECC, RAID                 | 讲座37：可靠性，奇偶校验，ECC，RAID                |
| P49  | Lecture 38: Data Centers, Warehouse Scale Computing          | 讲座38：数据中心，仓库级计算                       |
| P50  | Lecture 39: Guest Lecture with James Percy from Apple        | 讲座39：Apple 的 James Percy 的客座讲座            |
| P51  | Lecture 40: Summary, What's Next?                            | 讲座40：总结，接下来是什么？                       |
