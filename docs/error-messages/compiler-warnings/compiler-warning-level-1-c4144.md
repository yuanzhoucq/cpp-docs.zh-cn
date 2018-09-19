---
title: 编译器警告 （等级 1） C4144 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4144
dev_langs:
- C++
helpviewer_keywords:
- C4144
ms.assetid: a37b445d-dbc6-43b4-8d95-ffd0e4225464
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ba9c1210247ad537f8fa1224c30b1c88d9c6b721
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109660"
---
# <a name="compiler-warning-level-1-c4144"></a>编译器警告 （等级 1） C4144

expression： 关系表达式用作 switch 表达式

指定的关系表达式用作的控制表达式[切换](../../cpp/switch-statement-cpp.md)语句。 布尔值，将提供相关联的 case 语句。 下面的示例生成 C4144:

```
// C4144.cpp
// compile with: /W1
int main()
{
   int i = 0;
   switch(!i) {   // C4144, remove the ! to resolve
      case 1:
         break;
      default:
         break;
   }
}
```