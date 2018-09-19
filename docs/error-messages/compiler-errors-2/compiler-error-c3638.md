---
title: 编译器错误 C3638 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3638
dev_langs:
- C++
helpviewer_keywords:
- C3638
ms.assetid: 8d8bc5ca-75aa-480e-b6b6-3178fab51b1d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f1d135dd69155de39b097d59cf139eb47354d4f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107651"
---
# <a name="compiler-error-c3638"></a>编译器错误 C3638

operator： 标准装箱和取消装箱转换运算符不能重新定义

编译器会定义转换运算符为每个托管类来支持隐式装箱。 此运算符不能重新定义。

有关详细信息，请参阅[隐式装箱](../../windows/boxing-cpp-component-extensions.md)。

下面的示例生成 C3638:

```
// C3638.cpp
// compile with: /clr
value struct V {
   V(){}
   static operator V^(V);   // C3638
};

int main() {
   V myV;
   V ^ pmyV = myV;   // operator supports implicit boxing
}
```