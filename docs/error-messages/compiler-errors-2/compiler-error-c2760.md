---
title: 编译器错误 C2760
ms.date: 11/04/2016
f1_keywords:
- C2760
helpviewer_keywords:
- C2760
ms.assetid: 585757fd-d519-43f3-94e5-50316ac8b90b
ms.openlocfilehash: 5680de2fe0364d7cdc5e7ef017bd298423ea4c21
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273657"
---
# <a name="compiler-error-c2760"></a>编译器错误 C2760

> 语法错误：应为 "*name1*" 而不是 "*name2*"

## <a name="remarks"></a>备注

有多种方法可导致此错误。 通常，它是由编译器无法识别的令牌序列引起的。

## <a name="example"></a>示例

在此示例中，转换运算符与无效运算符一起使用。

```cpp
// C2760.cpp
class B {};
class D : public B {};

void f(B* pb) {
    D* pd1 = static_cast<D*>(pb);
    D* pd2 = static_cast<D*>=(pb);  // C2760
    D* pd3 = static_cast<D*=(pb);   // C2760
}
```
