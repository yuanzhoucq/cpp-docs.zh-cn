---
title: 编译器警告（等级1） C4183
ms.date: 11/04/2016
f1_keywords:
- C4183
helpviewer_keywords:
- C4183
ms.assetid: dc48312c-4b34-44dd-80ff-eb5f11d5ca47
ms.openlocfilehash: be79c664f09f80d8f0c8779babf236dccac90ea8
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626229"
---
# <a name="compiler-warning-level-1-c4183"></a>编译器警告（等级1） C4183

"identifier"：缺少返回类型;假定为返回 "int" 的成员函数

类或结构中成员函数的内联定义没有返回类型。 假定此成员函数的默认返回类型为 `int`。

下面的示例生成 C4183：

```cpp
// C4183.cpp
// compile with: /W1 /c
#pragma warning(disable : 4430)
class MyClass1;
class MyClass2 {
   MyClass1() {};   // C4183
};
```