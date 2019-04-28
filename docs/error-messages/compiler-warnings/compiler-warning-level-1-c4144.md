---
title: 编译器警告 （等级 1） C4144
ms.date: 11/04/2016
f1_keywords:
- C4144
helpviewer_keywords:
- C4144
ms.assetid: a37b445d-dbc6-43b4-8d95-ffd0e4225464
ms.openlocfilehash: b2406357baf70e45566f2d2f25839d151bac4186
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352944"
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