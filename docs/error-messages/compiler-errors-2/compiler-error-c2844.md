---
title: 编译器错误 C2844
ms.date: 11/04/2016
f1_keywords:
- C2844
helpviewer_keywords:
- C2844
ms.assetid: dcaf4cd2-21b0-4280-ae42-0a706c524d83
ms.openlocfilehash: 2676a32cee487595a2241359496ae9b0380126b8
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "58775006"
---
# <a name="compiler-error-c2844"></a>编译器错误 C2844

member： 不能为接口 interface 的成员

[接口类](../../extensions/interface-class-cpp-component-extensions.md)不能包含数据成员，除非它也是一个属性。

在接口中不允许属性或成员函数之外的任何内容。 此外，不允许构造函数、 析构函数和运算符。

下面的示例生成 C2844:

```
// C2844a.cpp
// compile with: /clr /c
public interface class IFace {
   int i;   // C2844
   // try the following line instead
   // property int Size;
};
```
