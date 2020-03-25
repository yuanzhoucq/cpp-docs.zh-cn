---
title: 编译器警告（等级1） C4067
ms.date: 11/04/2016
f1_keywords:
- C4067
helpviewer_keywords:
- C4067
ms.assetid: 1d10353e-8cd5-4b01-9184-a06189b965a4
ms.openlocfilehash: 8bdd16f5c3182e4217e195475bdb4a9a0f60fa6f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164113"
---
# <a name="compiler-warning-level-1-c4067"></a>编译器警告（等级1） C4067

> 预处理器指令后有意外标记-应输入换行符

## <a name="remarks"></a>备注

编译器发现并忽略了预处理器指令后面的额外字符。 这可能是由任何意外的字符引起的，但常见的原因是指令后面的分号不受使用。 注释不会导致此警告。 对于比默认设置更多的预处理器指令， **/za**编译器选项启用此警告。

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

若要解决此警告，请删除游离字符，或将其移到注释块中。 可以通过删除 **/za**编译器选项来禁用某些 C4067 警告。

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
