---
title: 编译器错误 C2857 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2857
dev_langs:
- C++
helpviewer_keywords:
- C2857
ms.assetid: b57302bd-58ec-45ae-992a-1e282d5eeccc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 49e94e12b4cdf07d9f7fe74dd481bbc032a937eb
ms.sourcegitcommit: 87d317ac62620c606464d860aaa9e375a91f4c99
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2018
ms.locfileid: "45601374"
---
# <a name="compiler-error-c2857"></a>编译器错误 C2857

> #include 语句中指定用 /Yc*文件名*源代码文件中找不到命令行选项

[/Yc](../../build/reference/yc-create-precompiled-header-file.md)选项可以指定不包含正在编译的源中的包含文件的名称。

## <a name="remarks"></a>备注

当你使用 **/Yc**<em>filename</em>源文件选项若要创建的预编译标头 (PCH) 文件，源文件必须包括*文件名*标头文件。 包含的源文件，直至并包括指定的每个文件*文件名*，包含在 PCH 文件。 使用编译的其他源文件中 **/Yu**<em>filename</em>选项以使用 PCH 文件的 include*文件名*必须是该文件中的第一个非注释行。 编译器将忽略之前包括源文件中的任何内容。

此错误可能引起`#include "filename"`不在 PCH 源文件中编译的条件编译块中的语句。

## <a name="example"></a>示例

在典型用法中，一个源项目文件中的指定为 PCH 源文件，和一个标头文件用作 PCH 头文件。 典型的 PCH 头文件包含所有库头文件使用在项目中，但不是本地仍处于开发阶段的标头。 在此示例中，名为 PCH 头文件*my_pch.h*。

```cpp
// my_pch.h
#pragma once
#include <stdio.h>
```

通过编译 PCH 源文件 **/Yc**<em>my_pch.h</em>选项。 如果编译器没有找到包括此 PCH 头文件，它将生成 C2857:

```cpp
// my_pch.cpp
// Compile by using: cl /EHsc /W4 /Yumy_pch.h /c my_pch.cpp

#if 0
#include "my_pch.h"  // C2857; remove conditional directives to fix
#endif
```

若要使用此 PCH 文件，必须使用将编译源文件 **/Yu**<em>my_pch.h</em>选项。 使用 PCH 的源文件中，必须首先包含 PCH 头文件：

```cpp
// C2857.cpp
// Compile my_pch.cpp first, then
// compile by using: cl /EHsc /W4 /Yumy_pch.h my_project.cpp my_pch.obj
// Include the pch header before any other non-comment line
#include "my_pch.h"

int main()
{
    puts("Using a precompiled header file.\n");
}
```