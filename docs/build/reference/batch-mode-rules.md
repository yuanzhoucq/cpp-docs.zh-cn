---
title: 批模式规则
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- NMAKE program, inference rules
- batch-mode inference rules in NMAKE
ms.assetid: 0650b547-ef19-4455-9bba-fa567dcf88f2
ms.openlocfilehash: 38402e7b8a937cebb823ce13fa1ac01fc1099878
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328413"
---
# <a name="batch-mode-rules"></a>批模式规则

```
{frompath}.fromext{topath}.toext::
   commands
```

当 N 命令通过此推理规则时，批处理模式推理规则仅提供一个推理规则的调用。 如果没有批处理模式推理规则，则需要调用 N 命令。 N 是触发推理规则的从属项数。

制作包含批处理模式推理规则的文件必须使用 NMAKE 版本 1.62 或更高版本。 要检查 NMAKE 版本，请运行与 NMAKE 版本 1.62 或更高版本的_NMAKE_VER宏。 此宏返回表示 VisualC++产品版本的字符串。

与标准推理规则的唯一语法区别是批处理模式推理规则终止了双冒号 （：:)。

> [!NOTE]
> 正在调用的工具必须能够处理多个文件。 批处理模式推理规则必须用作`$<`宏才能访问相关文件。

批处理模式推理规则可以加快生成过程。 批量向编译器提供文件会更快，因为编译器驱动程序只调用一次。 例如，在处理一组文件时，C 和C++编译器性能更好，因为它可以在过程中保持内存驻留。

下面的示例演示如何使用批处理模式推理规则：

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

NMAKE 生成以下输出，无需批处理模式推理规则：

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

NMAKE 使用批处理模式推理规则生成以下结果：

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

## <a name="see-also"></a>另请参阅

[推理规则](inference-rules.md)
