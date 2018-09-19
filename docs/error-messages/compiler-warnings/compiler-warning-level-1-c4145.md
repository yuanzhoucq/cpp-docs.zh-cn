---
title: 编译器警告 （等级 1） C4145 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4145
dev_langs:
- C++
helpviewer_keywords:
- C4145
ms.assetid: 0440777a-cca2-4159-aff5-e67a254ad64a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 65d041b9fdb7fb4b01abfadf5010444b0e406220
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100667"
---
# <a name="compiler-warning-level-1-c4145"></a>编译器警告（等级 1）C4145

“expression1”: 关系表达式用作 switch 表达式；可能和“expression2”混淆

`switch` 语句使用关系表达式作为其控制表达式，这会导致的 **case** 语句的布尔值。 是否希望使用 *expression2*?

## <a name="example"></a>示例

下面的示例生成 C4145:

```
// C4145.cpp
// compile with: /W1
int main() {
   int i = 0;
   switch(i == 1) {   // C4145, use i instead of i == 1 to resolve
      case 1:
         break;
      default:
         break;
   }
}
```