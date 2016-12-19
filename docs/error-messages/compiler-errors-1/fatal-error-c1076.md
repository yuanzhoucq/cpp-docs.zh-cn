---
title: "错误 C1076 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1076"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1076"
ms.assetid: 84ac1180-3e8a-48e8-9f77-7f18a778b964
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1076
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

编译器限制 : 达到内部堆限制；使用 \/Zm 指定更高的限制  
  
 此错误可能是由过多符号或过多模板实例化引起的。  
  
 解决此问题的方法是：  
  
1.  使用 [\/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) 选项将编译器内存限制设置为 [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md) 错误消息中指定的值。  有关包含如何在 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 中设置此值的详细信息，请参阅 [\/Zm（指定预编译头的内存分配限额）](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)中的“备注”部分。  
  
2.  如果正在 64 位操作系统中使用 32 位托管编译器，请改用 64 位托管编译器。  有关详细信息，请参阅[如何：在命令行上启用 64 位 Visual C\+\+ 工具集](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)。  
  
3.  消除不需要的包含文件。  
  
4.  消除不需要的全局变量，例如，动态分配内存而不是声明一个大数组。  
  
5.  消除未使用的声明。  
  
6.  将大函数拆分为更小的函数。  
  
7.  将大类拆分为更小的类。  
  
8.  将当前文件拆分成更小的文件。  
  
 如果在生成开始后立即发生 C1076，则说明为 **\/Zm** 指定的值对程序而言可能太高。  请减小 **\/Zm** 的值。