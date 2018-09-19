---
title: 编译器警告 （等级 1） C4627 |Microsoft Docs
ms.custom: ''
ms.date: 09/09/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4627
dev_langs:
- C++
helpviewer_keywords:
- C4627
ms.assetid: 8840f3e6-b496-423a-8635-eb55d5f854a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fef8d0ab55205d2377fc52049c40a1c50151b93e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024172"
---
# <a name="compiler-warning-level-1-c4627"></a>编译器警告（等级 1）C4627

> '*header_file*： 在查找预编译标头使用时跳过

如果当前源文件[/Yu\(使用预编译头文件)](../../build/reference/yu-use-precompiled-header-file.md)选项集，则编译器将忽略该文件中的所有内容，包含预编译标头之前。 警告**C4627**如果在 Visual Studio 2015 及更早版本中生成*header_file*包含之前预编译的头文件中，如果预编译标头还包括*header_file*。

## <a name="example"></a>示例

此示例演示如何错误不会发生，并演示如何修复此错误：

```cpp
// c4627.cpp
#include <iostream>       // C4627 - iostream not included by pch.h
#include "pch.h"          // precompiled header file that does not include iostream
// #include <iostream>    // To fix, move the iostream header include here from above
int main()
{
    std::cout << "std::cout is defined!\n";
}
```

## <a name="see-also"></a>请参阅

[创建预编译标头文件](../../build/reference/creating-precompiled-header-files.md)
