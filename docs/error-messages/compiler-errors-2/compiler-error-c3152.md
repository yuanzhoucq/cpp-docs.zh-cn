---
title: 编译器错误 C3152
ms.date: 11/04/2016
f1_keywords:
- C3152
helpviewer_keywords:
- C3152
ms.assetid: 4ee6e2cd-5d19-4b73-833d-765c35797e4b
ms.openlocfilehash: 52fa349b735a228a6acbe2fd6e1af461db2cf5c9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745936"
---
# <a name="compiler-error-c3152"></a>编译器错误 C3152

“construct”:“keyword”只能应用于类、结构或虚拟成员函数

某些关键字只能应用于 C++ 类。

下面的示例生成 C3152，并演示如何修复此错误：

```cpp
// C3152.cpp
// compile with: /clr /c
ref class C {
   int (*pfn)() sealed;   // C3152
   virtual int g() sealed;   // OK
};
```
