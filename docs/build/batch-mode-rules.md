---
title: "批模式规则 | Microsoft Docs"
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
helpviewer_keywords: 
  - "NMAKE 中的批模式推理规则"
  - "NMAKE 中的推理规则"
  - "NMAKE 程序, 推理规则"
ms.assetid: 0650b547-ef19-4455-9bba-fa567dcf88f2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 批模式规则
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

```  
{frompath}.fromext{topath}.toext::  
   commands  
```  
  
 当 N 条命令通过推理规则时，批模式推理规则只调用一次该推理规则。  如果没有批模式推理规则，将需要调用 N 条命令。  N 是触发推理规则的依赖项的数目。  
  
 包含批模式推理规则的生成文件必须使用 NMAKE 1.62 版或更高版。  若要检查 NMAKE 版本，请运行 NMAKE 1.62 版或更高版可用的 \_NMAKE\_VER 宏。  此宏返回表示 Visual C\+\+ 产品版本的字符串。  
  
 与标准推理规则相比，唯一的语法差别是：批模式推理规则以两个冒号 \(::\) 终止。  
  
> [!NOTE]
>  正在调用的工具必须能够处理多个文件。  批模式推理规则必须将 `$<` 用作宏来访问依赖文件。  
  
 批模式推理规则可以加快生成过程。  因为编译器驱动程序只调用一次，所以按批给编译器提供文件更快。  例如，C 和 C\+\+ 编译器在处理一组文件时性能更佳，因为它可以在处理期间使内存保持驻留。  
  
 下面的示例显示了如何使用批模式推理规则：  
  
```  
#  
# sample makefile to illustrate batch-mode inference rules  
#  
O = .  
S = .  
Objs = $O/foo1.obj $O/foo2.obj $O/foo2.obj $O/foo3.obj $O/foo4.obj  
CFLAGS = -nologo  
  
all : $(Objs)  
  
!ifdef NOBatch  
{$S}.cpp{$O}.obj:  
!else  
{$S}.cpp{$O}.obj::  
!endif  
   $(CC) $(CFLAGS) -Fd$O\ -c $<  
  
$(Objs) :  
  
#end of makefile  
```  
  
 如果不使用批模式推理规则，NMAKE 产生以下输出：  
  
```  
E:\tmp> nmake -f test.mak -a NOBatch=1  
  
Microsoft (R) Program Maintenance Utility   Version 7.00.0000  
Copyright (C) Microsoft Corp 1988-2001. All rights reserved.  
        cl -nologo -Fd.\ -c .\foo1.cpp  
foo1.cpp  
        cl -nologo -Fd.\ -c .\foo2.cpp  
foo2.cpp  
        cl -nologo -Fd.\ -c .\foo3.cpp  
foo3.cpp  
        cl -nologo -Fd.\ -c .\foo4.cpp  
foo4.cpp  
```  
  
 使用批模式推理规则，NMAKE 产生以下结果：  
  
```  
E:\tmp> nmake -f test.mak -a  
  
Microsoft (R) Program Maintenance Utility   Version 7.00.0000  
Copyright (C) Microsoft Corp 1988-2001. All rights reserved.  
  
        cl -nologo -Fd.\ -c .\foo1.cpp .\foo2.cpp .\foo3.cpp .\foo4.cpp  
foo1.cpp  
foo2.cpp  
foo3.cpp  
foo4.cpp  
Generating Code...  
```  
  
## 请参阅  
 [推理规则](../build/inference-rules.md)