---
title: 编译器错误 C2753
ms.date: 11/04/2016
f1_keywords:
- C2753
helpviewer_keywords:
- C2753
ms.assetid: 92bfeeac-524a-4a8e-9a4f-fb8269055826
ms.openlocfilehash: ea2901c998ac1a44ad142779e7ce48bfffff66c2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202140"
---
# <a name="compiler-error-c2753"></a>编译器错误 C2753

"*template*"：部分专用化无法与主模板的参数列表匹配

如果模板参数列表与参数列表匹配，则编译器会将其视为相同的模板。 不允许两次定义同一模板。

## <a name="example"></a>示例

下面的示例生成 C2753，并演示如何修复此问题：

```cpp
// C2753.cpp
// compile with: cl /c C2753.cpp
template<class T>
struct A {};

template<class T>
struct A<T> {};   // C2753
// try the following line instead
// struct A<int> {};

template<class T, class U, class V, class W, class X>
struct B {};
```
