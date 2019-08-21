---
title: 链接器工具警告 LNK4221
ms.date: 08/19/2019
f1_keywords:
- LNK4221
helpviewer_keywords:
- LNK4221
ms.assetid: 8e2eb2de-9532-4b85-908a-8c9ff5c4cccb
ms.openlocfilehash: 299c3ef76006b347d6770d45ca317ff0eb941ffa
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630806"
---
# <a name="linker-tools-warning-lnk4221"></a>链接器工具警告 LNK4221

此对象文件未定义任何之前未定义的公共符号, 因此任何使用此库的链接操作都不会使用它

请考虑以下两个代码片段。

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

若要编译文件和创建两个对象文件, 请在命令提示符下运行**cl/c a .cpp b.** 。 如果通过运行**链接/lib/out:** LNK4221 链接对象文件, 则将收到 "" 警告。 如果通过运行**链接/lib/out: test.txt a .obj**链接对象, 则不会收到警告。

在第二种情况下不会发出任何警告, 因为链接器以后进先出 (LIFO) 的方式运行。 在第一个方案中, 先处理 .obj, 然后再处理 .obj, 而 .obj 没有要添加的新符号。 通过指示链接器首先处理 .obj, 你可以避免出现此警告。

::: moniker range=">=vs-2019"

此错误的一个常见原因是两个源文件使用**预编译标头**字段中指定的同一标头文件名指定选项[/Yc (创建预编译标头文件)](../../build/reference/yc-create-precompiled-header-file.md) 。 此问题的一个常见原因是处理*pch* , 因为默认情况下, *pch*包含*pch* , 不添加任何新符号。 如果另一个源文件包含带有 **/yc**的*pch* , 并在 pch 之前处理相关的 .obj 文件, 则链接器将引发 LNK4221。

::: moniker-end

::: moniker range="<=vs-2017"

此错误的一个常见原因是两个源文件使用**预编译标头**字段中指定的同一标头文件名指定选项[/Yc (创建预编译标头文件)](../../build/reference/yc-create-precompiled-header-file.md) 。 此问题的一个常见原因是*stdafx.h* , 因为默认情况下, *stdafx.h*包含*stdafx.h* , 不添加任何新符号。 如果另一个源文件包含带有 **/yc**的*stdafx.h*并且在 stdafx.h 之前处理关联的 .obj 文件, 则链接器将引发 LNK4221。

::: moniker-end

解决此问题的一种方法是, 确保对于每个预编译标头, 只有一个源文件与 **/yc**一起包含。 所有其他源文件必须使用预编译头。 有关如何更改此设置的详细信息, 请参阅[/yu (使用预编译标头文件)](../../build/reference/yu-use-precompiled-header-file.md)。
