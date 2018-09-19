---
title: 编译器错误 C3865 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3865
dev_langs:
- C++
helpviewer_keywords:
- C3865
ms.assetid: 9bc62bb0-4fb8-4856-a5cf-c7cb4029a596
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8fd5c83d922601ca4cdffe0f3772723b31e630b6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090836"
---
# <a name="compiler-error-c3865"></a>编译器错误 C3865

calling_convention： 只能在本机成员函数上使用

已全局函数的函数或托管的成员函数上使用的调用约定。 仅在本机 （非托管） 的成员函数上可用的调用约定。

有关详细信息，请参阅[调用约定](../../cpp/calling-conventions.md)。

下面的示例生成 C3865:

```
// C3865.cpp
// compile with: /clr
// processor: x86
void __thiscall Func(){}   // C3865

// OK
struct MyType {
   void __thiscall Func(){}
};
```