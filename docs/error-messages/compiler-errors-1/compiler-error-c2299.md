---
title: 编译器错误 C2299
ms.date: 11/04/2016
f1_keywords:
- C2299
helpviewer_keywords:
- C2299
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
ms.openlocfilehash: 39659baebf7dc1859a69021f60ed452964ae61af
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447962"
---
# <a name="compiler-error-c2299"></a>编译器错误 C2299

function： 行为更改： 显式专用化不能复制构造函数或复制赋值运算符

此外可以为 Visual Studio 2005 执行的编译器一致性工作生成此错误： 以前版本的视觉对象C++复制构造函数或复制赋值运算符允许显式专用化。

若要解决 C2299，请不要复制构造函数或赋值运算符的模板函数，但而不是采用类类型的非模板函数。 通过显式指定模板自变量调用复制构造函数或赋值运算符的任何代码需要删除模板自变量。

下面的示例生成 C2299:

```
// C2299.cpp
// compile with: /c
class C {
   template <class T>
   C (T t);

   template <> C (const C&);   // C2299
   C (const C&);   // OK
};
```