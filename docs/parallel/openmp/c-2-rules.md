---
title: C.2 规则
ms.date: 11/04/2016
ms.assetid: 4d52fef7-3eb7-4480-a335-8ed48681092b
ms.openlocfilehash: 7c0de4c14e229716bcf764d9859be439090368b1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642801"
---
# <a name="c2-rules"></a>C.2 规则

表示法是部分所述 6.1 C 标准。 此语法附录显示 OpenMP C 和 c + + 指令的基本语言语法的扩展。

**/\* 在 c + + (ISO/IEC 14882:1998) \*/**

*语句-seq*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp 指令*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*语句-seq 语句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*语句-seq openmp 指令*

**/\* 在 C90 (ISO/IEC 9899:1990) \*/**

statement-list：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp 指令*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*语句列表语句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*语句列表 openmp 指令*

**/\* 在 C99 (ISO/IEC 9899:1999) \*/**

*阻止项*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp 指令*

**/\* 标准语句 \*/**

*statement*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp 构造*

*openmp 构造*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*并行构造*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*有关构造*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*部分构造*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*单构造*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*并行的构造*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*并行部分构造*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*master 构造*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*critical 构造*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*atomic 构造*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*有序构造*

*openmp 指令*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*barrier 指令*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*flush 指令*

*结构化块*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement*

*并行构造*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*并行指令结构化块*

*并行指令*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp 并行***并行子句*<sub>optseq</sub> *新行*

*并行子句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*唯一并行子句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*数据子句*

*唯一并行子句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**如果 (** *表达式* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**num_threads (** *表达式* **)**

*有关构造*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*指令的迭代语句*

*有关指令*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**为 # pragma omp** *for 子句*<sub>optseq</sub> *新行*

*for 子句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*唯一 for 子句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*数据子句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**nowait**

*唯一的子句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**排序**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**计划 (** *安排类型* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**计划 (** *安排类型* **，** *表达式* **)**

*计划类型*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**static**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**动态**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**引导式**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**运行时**

*部分构造*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sections 指令部分作用域*

*sections 指令*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp 部分***部分子句*<sub>optseq</sub> *新行*

*部分子句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*数据子句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**nowait**

*部分范围*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*{部分序列}*

*部分序列*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*区域指令*<sub>opt</sub> *结构化块*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*部分序列区域指令结构化块*

*区域指令*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp 部分***新行*

*单构造*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*单指令结构化块*

*单指令*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp 单一***单子句*<sub>optseq</sub> *新行*

*单子句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*数据子句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**nowait**

*并行的构造*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*并行的指令迭代语句*

*并行的指令*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**有关并行的 # pragma omp** *并行 for 子句*<sub>optseq</sub> *新行*

*并行 for 子句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*唯一并行子句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*唯一 for 子句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*数据子句*

*并行部分构造*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*并行 sections 指令部分作用域*

*并行 sections 指令*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp 并行段***并行部分子句*<sub>optseq</sub> *新行*

*并行部分子句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*唯一并行子句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*数据子句*

*主构造*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*master 指令结构化块*

*master 指令*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp master** *新行*

*critical 构造*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*关键指令结构化块*

*关键指令*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**关键的 # pragma omp** *区域短语*<sub>优化</sub>*新行*

*区域短语*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*（标识符）*

*屏障指令*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp 屏障***新行*

*atomic 构造*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*原子指令表达式语句*

*原子指令*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp atomic** *新行*

*flush 指令*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**刷新的 # pragma omp** *flush vars*<sub>优化</sub>*新行*

*刷新 vars*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*（变量列表）*

*有序构造*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*排序指令结构化块*

*排序指令*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp 排序***新行*

**/\* 标准声明 \*/**

*declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*threadprivate 指令*

*threadprivate 指令*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**# pragma omp threadprivate (** *变量列表***)** *新行*

*数据子句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**专用 (** *变量列表* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**copyprivate (***变量列表***)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**firstprivate (***变量列表***)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**lastprivate (** *变量列表***)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**共享 (** *变量列表* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**默认 （共享）**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**默认 （无）**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**减少 (***reduction 运算符***:***变量列表***)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**copyin (***变量列表***)**

*reduction 运算符*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;之一：  **+  \* -& ^ &#124; & &&#124;&#124;**

**/\* 在 C 中 \*/**

*变量列表*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*变量列表* **，** *标识符*

**/\* 在 c + + \*/**

*变量列表*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*id 表达式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*变量列表* **，** *id 表达式*