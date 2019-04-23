---
title: 编译器错误 C2483
ms.date: 09/15/2017
f1_keywords:
- C2483
helpviewer_keywords:
- C2483
ms.assetid: 5762b325-914b-442d-a604-e4617ba04038
ms.openlocfilehash: 7a627ce28e60f42dabcf0a257464a8bfbd58b9a4
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59028614"
---
# <a name="compiler-error-c2483"></a>编译器错误 C2483

>'*标识符*： 用构造函数或析构函数的对象不能声明为线程

此错误消息是在 Visual Studio 2015 及更高版本中已过时。 在早期版本中，变量声明与`thread`属性不能使用构造函数或其他需要运行时计算的表达式进行初始化。 初始化所需的静态表达式`thread`数据。

## <a name="example"></a>示例

下面的示例生成 C2483 Visual Studio 2013 和早期版本中。

```cpp
// C2483.cpp
// compile with: /c
__declspec(thread) struct A {
   A(){}
   ~A(){}
} aa;   // C2483 error

__declspec(thread) struct B {} b;   // OK
```

## <a name="see-also"></a>请参阅

[thread](../../cpp/thread.md)