---
title: 编译器错误 C2857
ms.date: 09/13/2018
f1_keywords:
- C2857
helpviewer_keywords:
- C2857
ms.assetid: b57302bd-58ec-45ae-992a-1e282d5eeccc
ms.openlocfilehash: 11b620f9748ac85e731d79b0652c0392375b2ea4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201846"
---
# <a name="compiler-error-c2857"></a>编译器错误 C2857

> 在源文件中找不到用/Yc*filename*命令行选项指定的 "#include" 语句

[/Yc](../../build/reference/yc-create-precompiled-header-file.md)选项指定不包含在要编译的源文件中的包含文件的名称。

## <a name="remarks"></a>备注

当你在源文件上使用 **/yc**<em>filename</em>选项来创建预编译标头（PCH）文件时，该源文件必须包含*filename*标头文件。 源文件包含的每个文件（包括指定的*文件名*）都包含在 PCH 文件中。 在使用 **/yu**<em>filename</em>选项编译的其他源文件中，若要使用 PCH 文件，文件中的第一个非注释行必须包含*filename* 。 编译器将忽略源文件中包含的任何内容。

此错误可能是由于未在 PCH 源文件中编译的条件编译块中的 `#include "filename"` 语句导致的。

## <a name="example"></a>示例

在典型的用法中，将项目中的一个源文件指定为 PCH 源文件，并使用一个头文件作为 PCH 标头文件。 典型的 PCH 标头文件包含在项目中使用的所有库标头，而不是仍处于开发阶段的本地标头。 在此示例中，PCH 标头文件的名称为*my_pch。*

```cpp
// my_pch.h
#pragma once
#include <stdio.h>
```

PCH 源文件是使用 **/yc**<em>my_pch .h</em>选项编译的。 如果编译器没有找到此 PCH 标头文件的包含，则会生成 C2857：

```cpp
// my_pch.cpp
// Compile by using: cl /EHsc /W4 /Yumy_pch.h /c my_pch.cpp

#if 0
#include "my_pch.h"  // C2857; remove conditional directives to fix
#endif
```

若要使用此 PCH 文件，必须使用 **/yu**<em>my_pch .h</em>选项来编译源文件。 PCH 头文件必须先包含在使用 PCH 的源文件中：

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
