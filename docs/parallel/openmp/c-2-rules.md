---
title: "C.2 规则 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 4d52fef7-3eb7-4480-a335-8ed48681092b
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e5efa8d0e7cf4118362b7695bafcd4710b4021f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="c2-rules"></a>C.2 规则
表示法是部分所述 6.1 C 标准。 此语法附录显示 OpenMP C 和 c + + 指令的基本语言语法的扩展。  
  
 **/\*在 c + + (ISO/IEC 14882:1998)\*/**  
  
 *语句 seq*:  
  
 statement  
  
 *openmp 指令*  
  
 *语句 seq 语句*  
  
 *语句 seq openmp 指令*  
  
 **/\*在 C90 (ISO/IEC 9899: 1990)\*/**  
  
 statement-list：  
  
 statement  
  
 *openmp 指令*  
  
 statement-list statement  
  
 *语句列表 openmp 指令*  
  
 **/\*在 C99 (ISO/IEC 9899: 1999)\*/**  
  
 *块项*:  
  
 declaration  
  
 statement  
  
 *openmp 指令*  
  
 *statement*：  
  
 **/\*标准语句\*/**  
  
 *openmp 构造*  
  
 *openmp 构造*:  
  
 *并行构造*  
  
 *有关构造*  
  
 *部分构造*  
  
 *单构造*  
  
 *并行的构造*  
  
 *并行部分构造*  
  
 *master construc*  
  
 *critical 构造*  
  
 *atomic 构造*  
  
 *排序构造*  
  
 *openmp 指令*:  
  
 *屏障指令*  
  
 *刷新指令*  
  
 *结构化块*:  
  
 statement  
  
 *并行构造*:  
  
 *并行指令结构化块*  
  
 *并行指令*:  
  
 **# pragma omp 并行***并行子句*optseq*新行*   
  
 *并行子句*:  
  
 *唯一并行子句*  
  
 *数据子句*  
  
 *唯一并行子句*:  
  
 **如果 (** *表达式* **)**  
  
 **num_threads (** *表达式* **)**  
  
 *有关构造*:  
  
 *指令为迭代语句*  
  
 *有关指令*:  
  
 **为 # pragma omp** *for 子句*optseq*新行*  
  
 *for 子句*:  
  
 *唯一 for 子句*  
  
 *数据子句*  
  
 **nowait**  
  
 *唯一 for 子句*:  
  
 **排序**  
  
 **计划 (** *计划类型* **)**  
  
 **计划 (** *计划类型* **，** *表达式* **)**  
  
 *计划类型*:  
  
 **static**  
  
 **动态**  
  
 **引导式**  
  
 **运行时**  
  
 *部分构造*:  
  
 *sections 指令部分作用域*  
  
 *sections 指令*:  
  
 **# pragma omp 部分***部分子句*optseq*新行*  
  
 *部分子句*:  
  
 *数据子句*  
  
 **nowait**  
  
 *部分范围*:  
  
 *{部分序列}*  
  
 *部分序列*:  
  
 *部分指令*选择*结构化块*  
  
 *部分序列部分指令结构化块*  
  
 *部分指令*:  
  
 **# pragma omp 部分***新行*  
  
 *单构造*:  
  
 *单指令结构化块*  
  
 *单指令*:  
  
 **# pragma omp 单个***单子句*optseq*新行*  
  
 *单子句*:  
  
 *数据子句*  
  
 **nowait**  
  
 *并行的构造*:  
  
 *并行的指令迭代语句*  
  
 *并行的指令*:  
  
 **有关并行的 # pragma omp** *并行 for 子句*optseq*新行*  
  
 *并行 for 子句*:  
  
 *唯一并行子句*  
  
 *唯一 for 子句*  
  
 *数据子句*  
  
 *并行部分构造*:  
  
 *并行 sections 指令部分作用域*  
  
 *并行 sections 指令*:  
  
 **# pragma omp 并行部分***并行部分子句*optseq*新行*  
  
 *并行部分子句*:  
  
 *唯一并行子句*  
  
 *数据子句*  
  
 *master 构造*:  
  
 *master 指令结构化块*  
  
 *master 指令*:  
  
 **# pragma omp master** *新行*  
  
 *critical 构造*:  
  
 *关键指令结构化块*  
  
 *关键指令*:  
  
 **# pragma omp 关键***区域短语*选择*新行*  
  
 *区域短语*:  
  
 *（标识符）*  
  
 *屏障指令*:  
  
 **# pragma omp 屏障***新行*  
  
 *atomic 构造*:  
  
 *原子指令表达式语句*  
  
 *原子指令*:  
  
 **# pragma omp atomic** *新行*  
  
 *刷新指令*:  
  
 **# pragma omp 刷新***刷新 var*选择*新行*  
  
 *刷新 var*:  
  
 *（变量列表）*  
  
 *排序构造*:  
  
 *排序指令结构化块*  
  
 *排序指令*:  
  
 **# pragma omp 排序***新行*  
  
 *声明*:  
  
 **/\*标准声明\*/**  
  
 *threadprivate 指令*  
  
 *threadprivate 指令*:  
  
 **# pragma omp threadprivate (** *变量列表***)** *新行*   
  
 *数据子句*:  
  
 **私有 (** *变量列表* **)**  
  
 **copyprivate (***变量列表***)**   
  
 **firstprivate (***变量列表***)**   
  
 **lastprivate (** *变量列表***)**   
  
 **共享 (** *变量列表* **)**  
  
 **默认值 （共享）**  
  
 **默认值 （无）**  
  
 **减少 (***reduction 运算符***:***变量列表***)**   
  
 **copyin (***变量列表***)**   
  
 *reduction 运算符*:  
  
 *之一*:  **+  \* -（& a) ^ &#124; & （& a) &#124; &#124;**  
  
 **/\*在 C 中\*/**  
  
 *变量列表*:  
  
 *identifier*  
  
 *变量列表* **，** *标识符*  
  
 **/\*在 c + +\*/**  
  
 *变量列表*:  
  
 *id 表达式*  
  
 *变量列表* **，** *id 表达式*