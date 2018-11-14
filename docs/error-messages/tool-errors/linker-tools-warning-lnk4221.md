---
title: 链接器工具警告 LNK4221
ms.date: 11/04/2016
f1_keywords:
- LNK4221
helpviewer_keywords:
- LNK4221
ms.assetid: 8e2eb2de-9532-4b85-908a-8c9ff5c4cccb
ms.openlocfilehash: baea8643001c550aeb3cb35dc6fe414e4330c0c1
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51523463"
---
# <a name="linker-tools-warning-lnk4221"></a>链接器工具警告 LNK4221

此对象文件未定义任何之前未定义的公共符号，因此它不使用任何耗用此库的链接操作

请考虑以下两个代码段。

```
// a.cpp
#include <atlbase.h>
```

```
// b.cpp
#include <atlbase.h>
int function()
{
   return 0;
}
```

若要编译的文件并创建两个对象文件，运行**cl /c a.cpp b.cpp**在命令提示符。 如果通过运行链接对象文件**链接/lib /out:test.lib a.obj b.obj**，你将收到 LNK4221 警告。 如果将对象链接通过运行**链接/lib /out:test.lib b.obj a.obj**，您将不会收到一条警告。

在第二个方案中会不发出任何警告，因为链接器以非后进先出 (LIFO) 方式工作。 在第一个方案中之前 a.obj，处理 b.obj 和 a.obj 有无新符号来添加。 指示链接器首先处理 a.obj，可以避免此警告。

此错误的常见原因是当两个源文件指定选项[/Yc （创建预编译标头文件）](../../build/reference/yc-create-precompiled-header-file.md)具有相同标头文件名称中指定**预编译标头**字段。 此问题的常见原因处理 stdafx.h 由于默认情况下，stdafx.cpp 包括 stdafx.h 并不会添加任何新的符号。 如果另一个源文件都包含与 stdafx.h **/Yc**和关联的.obj 文件中，在处理时会先 stdafx.obj，链接器将引发 LNK4221。

一种方法来解决此问题是，确保为每个预编译标头，存在是只有一个源文件，其中包括其与 **/Yc**。 所有其他源文件必须使用预编译标头。 有关如何更改此设置的详细信息，请参阅[/Yu （使用预编译标头文件）](../../build/reference/yu-use-precompiled-header-file.md)。