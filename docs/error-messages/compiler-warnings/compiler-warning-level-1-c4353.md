---
title: 编译器警告 （等级 1） C4353 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4353
dev_langs:
- C++
helpviewer_keywords:
- C4353
ms.assetid: 6e79f186-ed82-4c95-9923-0ad5bb9c4db1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3926de61cdc41464c14c8610fee3033d10076506
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066838"
---
# <a name="compiler-warning-level-1-c4353"></a>编译器警告（等级 1）C4353

使用了非标准扩展： 常量 0 作为了函数表达式。 请改用 __noop 函数内部函数

不能使用常数零 (0) 作为了函数表达式。 有关详细信息，请参阅[__noop](../../intrinsics/noop.md)。

下面的示例生成 C4353:

```
// C4353.cpp
// compile with: /W1
void MyPrintf(void){};
#define X 0
#if X
   #define DBPRINT MyPrint
#else
   #define DBPRINT 0   // C4353 expected
#endif
int main(){
DBPRINT();
}
```