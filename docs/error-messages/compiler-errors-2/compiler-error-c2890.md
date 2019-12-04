---
title: 编译器错误 C2890
ms.date: 11/04/2016
f1_keywords:
- C2890
helpviewer_keywords:
- C2890
ms.assetid: 49147375-182c-42b1-b170-f475cd436d47
ms.openlocfilehash: d51748e80dad0370b5f735180455dd6c8d113c7a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760897"
---
# <a name="compiler-error-c2890"></a>编译器错误 C2890

"class"： ref 类只能有一个非接口基类

引用类只能有一个基类。

下面的示例生成 C2890：

```cpp
// C2890.cpp
// compile with: /clr /c
ref class A {};
ref class B {};
ref class C : public A, public B {};   // C2890
ref class D : public A {};   // OK
```
