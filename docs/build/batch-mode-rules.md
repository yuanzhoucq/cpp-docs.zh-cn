---
title: 批模式规则 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inference rules in NMAKE
- NMAKE program, inference rules
- batch-mode inference rules in NMAKE
ms.assetid: 0650b547-ef19-4455-9bba-fa567dcf88f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2b002b17fcc70ff4e374fb0630e9c18a52cbfc4f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361439"
---
# <a name="batch-mode-rules"></a>批模式规则
```  
{frompath}.fromext{topath}.toext::  
   commands  
```  
  
 在 N 条命令经历此推理规则时，批模式推理规则提供推理规则仅一次的调用。 不使用批模式推理规则，它将需要调用 N 命令。 N 是触发推理规则的依赖项的数目。  
  
 包含批模式推理规则生成文件必须使用 NMAKE 1.62 或更高版本。 若要检查的 NMAKE 版本，运行 _NMAKE_VER 宏可用用于 NMAKE 版本 1.62 或更高版本。 此宏将返回表示的 Visual c + + 产品版本的字符串。  
  
 从标准的推理规则仅语法上的差异是： 批模式推理规则以使用两个冒号 （:）  
  
> [!NOTE]
>  正在调用的工具必须能够处理多个文件。 批模式推理规则必须使用`$<`用作宏来访问依赖文件。  
  
 批模式推理规则可以加快生成过程。 将更快地提供文件添加到批处理中，编译器由于一次调用编译器驱动程序。 例如，C 和 c + + 编译器将执行更好地处理一组文件，因为它可以保持内存驻留在过程中时。  
  
 下面的示例演示如何使用批模式推理规则：  
  
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
  
 NMAKE 产生不使用批模式推理规则下面的输出：  
  
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
  
 NMAKE 产生以下结果与批模式推理规则：  
  
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
  
## <a name="see-also"></a>请参阅  
 [推理规则](../build/inference-rules.md)