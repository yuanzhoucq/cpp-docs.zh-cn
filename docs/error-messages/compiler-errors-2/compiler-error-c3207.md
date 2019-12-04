---
title: 编译器错误 C3207
ms.date: 11/04/2016
f1_keywords:
- C3207
helpviewer_keywords:
- C3207
ms.assetid: 4a28b976-142a-4cff-aa2f-480b892c50ca
ms.openlocfilehash: 718c731985e6578787d190c70cb8041bd85ab8e7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751064"
---
# <a name="compiler-error-c3207"></a>编译器错误 C3207

“function”：“arg”的模板参数无效，应当是类模板

将模板函数定义为采用模板模板参数。 但是，传递的是模板类型参数。

以下示例生成 C3207：

```cpp
// C3207.cpp
template <template <class T> class TT>
void f(){}

template <class T>
struct S
{
};

void f1()
{
   f<S<int> >();   // C3207
   // try the following line instead
   // f<S>();
}
```
