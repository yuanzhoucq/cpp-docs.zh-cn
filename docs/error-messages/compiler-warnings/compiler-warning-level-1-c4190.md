---
title: 编译器警告 （等级 1） C4190
ms.date: 11/04/2016
f1_keywords:
- C4190
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
ms.openlocfilehash: 05984594a57878aad8037861a15ac9284ff65192
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386494"
---
# <a name="compiler-warning-level-1-c4190"></a>编译器警告 （等级 1） C4190

identifier1 具有 C 链接指定，但它返回 UDT 与 C 不兼容的 identifier2

函数指针作为返回类型具有 UDT （用户定义类型，这是类、 结构、 枚举或联合） 和`extern`"C"链接。 这是合法如果：

- 对此函数的所有调用都发生从C++。

- 函数的定义是在C++。

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