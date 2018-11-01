---
title: 编译器错误 C2912
ms.date: 11/04/2016
f1_keywords:
- C2912
helpviewer_keywords:
- C2912
ms.assetid: bd55cecd-ab1a-4636-ab8a-a00393fe7b3d
ms.openlocfilehash: b7f87ae2df5350fcfb2b7a662f517d8d7bd51ef8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540070"
---
# <a name="compiler-error-c2912"></a>编译器错误 C2912

显式专用化“declaration”不是函数模板的专用化

无法特化非模板函数。

以下示例生成 C2912：

```
// C2912.cpp
// compile with: /c
void f(char);
template<> void f(char);   // C2912
template<class T> void f(T);   // OK
```

此外，在 Visual Studio .NET 2003 中完成的编译器一致性工作也会导致生成此错误：对于每个显式专用化，必须选择显式专用化参数，只有这样它们才会匹配主模板的参数。

```
// C2912b.cpp
class CF {
public:
   template <class A> CF(const A& a) {}   // primary template

   // attempted explicit specialization
   template <> CF(const char* p) {}   // C2912

   // try the following line instead
   // template <> CF(const char& p) {}
};
```