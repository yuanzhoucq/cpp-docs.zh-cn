---
title: 编译器错误 C3299
ms.date: 11/04/2016
f1_keywords:
- C3299
helpviewer_keywords:
- C3299
ms.assetid: 7cabdf01-bceb-404f-9401-cdd9c7fc1641
ms.openlocfilehash: 314b75a9d0ab8cde2886a7466fa0f95b5bbdd8f1
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "58778047"
---
# <a name="compiler-error-c3299"></a>编译器错误 C3299

“member_function”：无法指定约束，因为它们都继承自基方法

替代泛型成员函数时，无法指定约束子句（重复约束意味着未继承约束）。

将继承正在替代的泛型函数上的约束子句。

有关详细信息，请参阅[泛型类型参数的约束 (C + + CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md)。

## <a name="example"></a>示例

下面的示例生成 C3299。

```
// C3299.cpp
// compile with: /clr /c
public ref struct R {
   generic<class T>
   where T : R
   virtual void f();
};

public ref struct S : R {
   generic<class T>
   where T : R   // C3299
   virtual void f() override;
};
```