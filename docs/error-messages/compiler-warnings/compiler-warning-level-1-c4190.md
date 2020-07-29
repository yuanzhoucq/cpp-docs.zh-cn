---
title: 编译器警告（等级1） C4190
ms.date: 11/04/2016
f1_keywords:
- C4190
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
ms.openlocfilehash: 8187926f2477a4d3f1ca3019cc8c3c71710c1dff
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233296"
---
# <a name="compiler-warning-level-1-c4190"></a>编译器警告（等级1） C4190

"identifier1" 指定了 C 链接，但返回了与 C 不兼容的 UDT "identifier2"

函数或指向函数的指针具有作为返回类型和链接的 UDT （用户定义的类型，该类型是类、结构、枚举或联合） `extern "C"` 。 这是合法的：

- 对此函数的所有调用都是从 c + + 发生的。

- 函数的定义是在 c + + 中。

## <a name="example"></a>示例

```cpp
// C4190.cpp
// compile with: /W1 /LD
struct X
{
   int i;
   X ();
   virtual ~X ();
};

extern "C" X func ();   // C4190
```
