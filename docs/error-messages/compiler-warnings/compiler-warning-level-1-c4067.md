---
title: 编译器警告 （等级 1） C4067 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4067
dev_langs:
- C++
helpviewer_keywords:
- C4067
ms.assetid: 1d10353e-8cd5-4b01-9184-a06189b965a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ee6b48327e8754f9388e0df8f43009a5be70c97
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="compiler-warning-level-1-c4067"></a>编译器警告 （等级 1） C4067

> 意外的令牌以下预处理器指令的预期换行符

## <a name="remarks"></a>备注

编译器发现，并忽略额外预处理器指令后的字符。 原因可能是由任何意外的字符，尽管的常见原因是孤立的分号执行该指令之后。 注释不会导致此警告。 **/Za**编译器选项，可以比默认设置的多个预处理器指令此警告。

## <a name="example"></a>示例

```cpp
// C4067a.cpp
// compile with: cl /EHsc /DX /W1 /Za C4067a.cpp
#include <iostream>
#include <string> s     // C4067
#if defined(X);         // C4067
std::string s{"X is defined"};
#else
std::string s{"X is not defined"};
#endif;                 // C4067 only under /Za
int main()
{
    std::cout << s << std::endl;
}
```

若要解决此警告，删除孤立的字符，或将它们移到一个注释块。 通过删除可能禁用了某些 C4067 警告 **/Za**编译器选项。

```cpp
// C4067b.cpp
// compile with: cl /EHsc /DX /W1 C4067b.cpp
#include <iostream>
#include <string>
#if defined(X)
std::string s{"X is defined"};
#else
std::string s{"X is not defined"};
#endif
int main()
{
    std::cout << s << std::endl;
}
```