---
title: 编译器错误 C2844 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2844
dev_langs:
- C++
helpviewer_keywords:
- C2844
ms.assetid: dcaf4cd2-21b0-4280-ae42-0a706c524d83
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5dd4cbdc30523563207fe2a66c1c5cb158f84c94
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092097"
---
# <a name="compiler-error-c2844"></a>编译器错误 C2844

member： 不能为接口 interface 的成员

[接口类](../../windows/interface-class-cpp-component-extensions.md)不能包含数据成员，除非它也是一个属性。

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
