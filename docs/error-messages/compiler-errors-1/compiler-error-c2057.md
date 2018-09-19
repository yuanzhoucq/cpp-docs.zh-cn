---
title: 编译器错误 C2057 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2057
dev_langs:
- C++
helpviewer_keywords:
- C2057
ms.assetid: 038a99d6-1f5a-42fa-8449-03b4ff11ee0b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb9018224d10fa0104ee461e8bbeb659173fc9f0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051709"
---
# <a name="compiler-error-c2057"></a>编译器错误 C2057

应输入常量表达式

该上下文要求输入常数表达式，即其值在编译时已知的表达式。

编译器在编译时必须知道类型的大小，以便为该类型的实例分配空间。

## <a name="example"></a>示例

下面的示例生成 C2057，并演示如何修复此错误：

```
// C2057.cpp
int i;
int b[i];   // C2057 - value of i is unknown at compile time
int main() {
   const int i = 8;
   int b[i]; // OK - value of i is fixed and known to compiler
}
```

## <a name="example"></a>示例

C 对常数表达式有限制性更强的规则。  下面的示例生成 C2057，并演示如何修复此错误：

```
// C2057b.c
#define ArraySize1 10
int main() {
   const int ArraySize2 = 10;
   int h[ArraySize2];   // C2057 - C does not allow variables here
   int h[ArraySize1];   // OK - uses preprocessor constant
}
```