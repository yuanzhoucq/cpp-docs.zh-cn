---
title: "C.2 规则 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 4d52fef7-3eb7-4480-a335-8ed48681092b
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C.2 规则
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示法是部分所述 6.1 C 标准。 此语法附录显示 OpenMP C 和 c + + 指令的基本语言语法的扩展。  
  
 **/\* 在 c + + (ISO/IEC 14882:1998) \*/**  
  
 *语句-seq*:  
  
 *语句*  
  
 *openmp 指令*  
  
 *语句-seq 语句*  
  
 *语句-seq openmp 指令*  
  
 **/\* 在 C90 (ISO/IEC 9899:1990) \*/**  
  
 *语句列表*:  
  
 *语句*  
  
 *openmp 指令*  
  
 *语句列表语句*  
  
 *语句列表 openmp 指令*  
  
 **/\* 在 C99 中 (ISO/IEC 9899:1999) \*/**  
  
 *块项*:  
  
 *声明*  
  
 *语句*  
  
 *openmp 指令*  
  
 *语句*:  
  
 **/\* 标准的语句 \*/**  
  
 *openmp 构造*  
  
 *openmp 构造*:  
  
 *并行构造*  
  
 *有关构造*  
  
 *部分构造*  
  
 *单构造*  
  
 *并行的构造*  
  
 *并行部分构造*  
  
 *母版 construc*  
  
 *critical 构造*  
  
 *atomic 构造*  
  
 *有序构造*  
  
 *openmp 指令*:  
  
 *barrier 指令*  
  
 *flush 指令*  
  
 *结构化块*:  
  
 *语句*  
  
 *并行构造*:  
  
 *并行指令构造块*  
  
 *并行指令*:  
  
 **# pragma omp 并行**  *并行子句*optseq *新行*  
  
 *并行子句*:  
  
 *唯一并行子句*  
  
 *data 子句*  
  
 *唯一并行子句*:  
  
 **如果 (** *表达式* **)**  
  
 **num_threads (** *表达式* **)**  
  
 *有关构造*:  
  
 *指令的迭代语句*  
  
 *有关指令*:  
  
 **为 # pragma omp** *for 子句*optseq *新行*  
  
 *for 子句*:  
  
 *唯一 for 子句*  
  
 *data 子句*  
  
 **nowait**  
  
 *唯一 for 子句*:  
  
 **排序**  
  
 **计划 (** *计划类型* **)**  
  
 **计划 (** *计划类型* **,，** *表达式* **)**  
  
 *计划类型*:  
  
 **静态**  
  
 **动态**  
  
 **引导式**  
  
 **运行时**  
  
 *部分构造*:  
  
 *sections 指令部分作用域*  
  
 *sections 指令*:  
  
 **# pragma omp 部分** *部分子句*optseq *新行*  
  
 *部分子句*:  
  
 *data 子句*  
  
 **nowait**  
  
 *部分范围*:  
  
 *{部分序列}*  
  
 *部分序列*:  
  
 *部分指令*选择 *构造块*  
  
 *结构化的部分序列部分指令的块*  
  
 *部分指令*:  
  
 **# pragma omp 部分** *新行*  
  
 *单构造*:  
  
 *单指令构造块*  
  
 *单指令*:  
  
 **# pragma omp 单个** *单子句*optseq *新行*  
  
 *单子句*:  
  
 *data 子句*  
  
 **nowait**  
  
 *并行的构造*:  
  
 *并行的指令迭代语句*  
  
 *并行的指令*:  
  
 **有关并行的 # pragma omp** *并行 for 子句*optseq *新行*  
  
 *并行 for 子句*:  
  
 *唯一并行子句*  
  
 *唯一 for 子句*  
  
 *data 子句*  
  
 *并行部分构造*:  
  
 *并行 sections 指令部分作用域*  
  
 *并行 sections 指令*:  
  
 **# pragma omp 并行段** *并行部分子句*optseq *新行*  
  
 *并行部分子句*:  
  
 *唯一并行子句*  
  
 *data 子句*  
  
 *主构造*:  
  
 *master 指令构造块*  
  
 *master 指令*:  
  
 **# pragma omp master** *新行*  
  
 *critical 构造*:  
  
 *critical 指令构造块*  
  
 *critical 指令*:  
  
 **# pragma omp 关键** *区域短语*选择 *新行*  
  
 *区域短语*:  
  
 *（标识符）*  
  
 *barrier 指令*:  
  
 **# pragma omp 屏障** *新行*  
  
 *atomic 构造*:  
  
 *atomic 指令表达式语句*  
  
 *atomic 指令*:  
  
 **# pragma omp 原子** *新行*  
  
 *flush 指令*:  
  
 **# pragma omp 刷新** *刷新 var*选择 *新行*  
  
 *刷新 var*:  
  
 *（变量列表）*  
  
 *有序构造*:  
  
 *按序指令构造块*  
  
 *按序指令*:  
  
 **# pragma omp 订购** *新行*  
  
 *声明*:  
  
 **/\* 标准声明 \*/**  
  
 *threadprivate 指令*  
  
 *threadprivate 指令*:  
  
 **# pragma omp threadprivate (** *变量列表*  **)** *新行*  
  
 *data 子句*:  
  
 **专用 (** *变量列表* **)**  
  
 **copyprivate (**  *变量列表*  **)**  
  
 **firstprivate (**  *变量列表*  **)**  
  
 **lastprivate (** *变量列表*  **)**  
  
 **共享 (** *变量列表* **)**  
  
 **默认值 （共享）**  
  
 **默认值 （无）**  
  
 **减少 (**  *缩减运算符*  **:**  *变量列表*  **)**  
  
 **copyin (**  *变量列表*  **)**  
  
 *减少运算符*:  
  
 *其中一个*: **+ \* -（& a) ^ & #124; （& a) （& a) （& a) #124; & #124;**  
  
 **/\* 在 C 中 \*/**  
  
 *变量列表*:  
  
 *标识符*  
  
 *变量列表* **,，** *标识符*  
  
 **/\* 在 c + + \*/**  
  
 *变量列表*:  
  
 *id 表达式*  
  
 *变量列表* **,，** *id 表达式*