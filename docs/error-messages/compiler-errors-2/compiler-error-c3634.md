---
title: 编译器错误 C3634
ms.date: 11/04/2016
f1_keywords:
- C3634
helpviewer_keywords:
- C3634
ms.assetid: fd09f10c-f863-483b-9756-71c16b760b02
ms.openlocfilehash: 2acd76fee5e7ca309991e639044a45ea83ed112b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385662"
---
# <a name="compiler-error-c3634"></a>编译器错误 C3634

function： 不能定义托管或 WinRTclass 的抽象方法

可在托管或 WinRT 类中声明一个抽象方法，但不能定义它。

## <a name="example"></a>示例

以下示例生成 C3634：

```
// C3634.cpp
// compile with: /clr
ref class C {
   virtual void f() = 0;
};

void C::f() {   // C3634 - don't define managed class' pure virtual method
}
```
