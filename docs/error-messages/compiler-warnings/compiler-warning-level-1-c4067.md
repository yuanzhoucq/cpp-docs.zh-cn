---
title: 编译器警告 （等级 1） C4067
ms.date: 11/04/2016
f1_keywords:
- C4067
helpviewer_keywords:
- C4067
ms.assetid: 1d10353e-8cd5-4b01-9184-a06189b965a4
ms.openlocfilehash: 012866e328433ec9511782c26a39265481ff4940
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50541176"
---
# <a name="compiler-warning-level-1-c4067"></a>编译器警告 （等级 1） C4067

> 意外的令牌以下预处理器指令-应输入换行符

## <a name="remarks"></a>备注

编译器找到并忽略额外预处理器指令后的字符。 原因可能是由任何意外的字符，尽管该指令之后的常见原因是孤立的分号。 注释不会导致此警告。 **/Za**编译器选项让多个预处理器指令的默认设置比此警告。

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

若要解决此警告，请删除孤立的字符，或将其移动到注释块。 通过删除可能会禁用某些 C4067 警告 **/Za**编译器选项。

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