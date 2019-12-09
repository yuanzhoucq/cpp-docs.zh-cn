---
title: 编译器错误 C2943
ms.date: 11/04/2016
f1_keywords:
- C2943
helpviewer_keywords:
- C2943
ms.assetid: ede6565e-d892-44c0-8eee-c69545f3be2e
ms.openlocfilehash: ac704c06ac0e455cccdb2b035d0947ae9ec04bd5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755390"
---
# <a name="compiler-error-c2943"></a>编译器错误 C2943

“class”：type-class-id 重新定义为模板的类形参数

你不能使用泛型类或模板类，而是改用符号作为泛型或模板类型参数。

以下示例生成 C2943：

```cpp
// C2943.cpp
// compile with: /c
template<class T>
class List {};

template<class List<int> > class MyList;   // C2943
template<class T >  class MyList;
```
