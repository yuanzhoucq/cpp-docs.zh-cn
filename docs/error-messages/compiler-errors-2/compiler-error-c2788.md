---
title: 编译器错误 C2788
ms.date: 11/04/2016
f1_keywords:
- C2788
helpviewer_keywords:
- C2788
ms.assetid: 8688fc5c-e652-43b4-b407-9c488c76f2db
ms.openlocfilehash: a708e711fd086d31ecd5e8cc9c35679571af48c4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739566"
---
# <a name="compiler-error-c2788"></a>编译器错误 C2788

"identifier"：多个与此对象关联的 GUID

[__Uuidof](../../cpp/uuidof-operator.md)运算符使用附加了 GUID 的用户定义类型或此类用户定义类型的对象。 如果参数是具有多个 Guid 的对象，则会发生此错误。

下面的示例生成 C2788：

```cpp
// C2788.cpp
#include <windows.h>
struct __declspec(uuid("00000001-0000-0000-0000-000000000000")) A {};
struct __declspec(uuid("{00000002-0000-0000-0000-000000000000}")) B {};
template <class T, class U> class MyClass {};

typedef MyClass<A,B> MyBadClass;
typedef MyClass<A,A> MyGoodClass;

int main() {
   __uuidof(MyBadClass);    // C2788
   // try the following line instead
   __uuidof(MyGoodClass);
}
```
