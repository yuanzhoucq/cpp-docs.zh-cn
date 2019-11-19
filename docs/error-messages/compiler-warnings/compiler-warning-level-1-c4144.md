---
title: 编译器警告（等级1） C4144
ms.date: 11/04/2016
f1_keywords:
- C4144
helpviewer_keywords:
- C4144
ms.assetid: a37b445d-dbc6-43b4-8d95-ffd0e4225464
ms.openlocfilehash: e780c2a4f83106bfa298ef5320ddc85daf2d44c4
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624985"
---
# <a name="compiler-warning-level-1-c4144"></a>编译器警告（等级1） C4144

"expression"：关系表达式用作 switch 表达式

指定的关系表达式用作[switch](../../cpp/switch-statement-cpp.md)语句的控制表达式。 将为关联的 case 语句提供布尔值。 下面的示例生成 C4144：

```cpp
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