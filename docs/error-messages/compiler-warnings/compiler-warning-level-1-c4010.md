---
title: 编译器警告（等级1） C4010
ms.date: 11/04/2016
f1_keywords:
- C4010
helpviewer_keywords:
- C4010
ms.assetid: d607a9ff-8f8f-45c0-b07b-3b2f439e5485
ms.openlocfilehash: 045b3f6e615e11c24caa9a088baf6ea9f6448efb
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627315"
---
# <a name="compiler-warning-level-1-c4010"></a>编译器警告（等级1） C4010

单行注释包含行继续符

由//引入的单行注释包含一个作为行继续符的反斜杠（\\）。 编译器将下一行视为延续，并将其视为注释。

某些语法定向编辑器不将继续符后面的行指示为注释。 忽略导致此警告的任何行的语法着色。

下面的示例生成 C4010：

```cpp
// C4010.cpp
// compile with: /WX
int main() {
   // the next line is also a comment because of the backslash \
   int a = 3; // C4010
   a++;
}
```