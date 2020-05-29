---
title: 编译器警告（等级 1）C4600
ms.date: 11/04/2016
f1_keywords:
- C4600
helpviewer_keywords:
- C4600
ms.assetid: f023a2a1-7fc4-463f-a434-dc93fcd3f4e9
ms.openlocfilehash: 15ad64ad29f6f01253a2329fb04897c299cedff9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186070"
---
# <a name="compiler-warning-level-1-c4600"></a>编译器警告（等级 1）C4600

\#杂注 "macro name"：应为有效的非空字符串

当使用[pop_macro](../../preprocessor/pop-macro.md)或[push_macro](../../preprocessor/push-macro.md)推送或弹出宏名称时，不能指定空字符串。

下面的示例生成 C4600：

```cpp
// C4600.cpp
// compile with: /W1
int main()
{
   #pragma push_macro("")   // C4600 passing an empty string
}
```
