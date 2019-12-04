---
title: 编译器错误 C2844
ms.date: 11/04/2016
f1_keywords:
- C2844
helpviewer_keywords:
- C2844
ms.assetid: dcaf4cd2-21b0-4280-ae42-0a706c524d83
ms.openlocfilehash: fdfd2200503f80addb120117ce06f5f837d6b9f2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752010"
---
# <a name="compiler-error-c2844"></a>编译器错误 C2844

"member"：不能是接口 "interface" 的成员

[接口类](../../extensions/interface-class-cpp-component-extensions.md)不能包含数据成员，除非它也是一个属性。

在接口中不允许使用属性或成员函数之外的任何内容。 此外，不允许使用构造函数、析构函数和运算符。

下面的示例生成 C2844：

```cpp
// C2844a.cpp
// compile with: /clr /c
public interface class IFace {
   int i;   // C2844
   // try the following line instead
   // property int Size;
};
```
