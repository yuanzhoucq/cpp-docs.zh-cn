---
title: 批模式规则
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- NMAKE program, inference rules
- batch-mode inference rules in NMAKE
ms.assetid: 0650b547-ef19-4455-9bba-fa567dcf88f2
ms.openlocfilehash: 106db69327bbad112be7efea6970845956e52431
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416665"
---
# <a name="batch-mode-rules"></a>批模式规则

```
{frompath}.fromext{topath}.toext::
   commands
```

批模式推理规则提供推理规则仅一次的调用时 N 命令经历此推断规则。 不批模式推理规则，它将要求要调用的 N 命令。 N 是触发推理规则的依赖项的数目。

包含批模式推理规则生成文件必须使用 NMAKE 1.62 或更高版本。 若要检查的 NMAKE 版本，运行 _NMAKE_VER 宏可用于 NMAKE 版本 1.62 或更高版本。 此宏将返回一个字符串，表示 Visual c + + 产品版本。

与标准的推理规则仅语法上的差异是： 批模式推理规则以双冒号 （:）

> [!NOTE]
>  正在调用的工具必须能够处理多个文件。 批模式推理规则必须使用`$<`为宏来访问依赖文件。

批模式推理规则可以加快生成过程。 它是更快地提供文件复制到的编译器中批处理，因为编译器驱动程序调用一次。 例如，C 和 c + + 编译器更好地执行将处理一组文件，因为它可以保持内存驻留在过程中时。

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

NMAKE 生成以下输出不批模式推理规则：

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

NMAKE 生成以下结果与批模式推理规则：

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
