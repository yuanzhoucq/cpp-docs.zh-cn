---
title: 编译器警告（等级 4）C4207
ms.date: 11/04/2016
f1_keywords:
- C4207
helpviewer_keywords:
- C4207
ms.assetid: f4e09e3e-ac87-4489-8e3f-c8f76b82e721
ms.openlocfilehash: e694f96d7f6271686d1b2a19e5a12e5e08e1cfbe
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219945"
---
# <a name="compiler-warning-level-4-c4207"></a>编译器警告（等级 4）C4207

使用了非标准扩展：扩展初始值设定项窗体

使用 Microsoft 扩展（/Ze），可以 **`char`** 使用大括号内的字符串初始化的成员列表数组数组。

## <a name="example"></a>示例

```c
// C4207.c
// compile with: /W4
char c[] = { 'a', 'b', "cdefg" }; // C4207

int main()
{
}
```

此类初始化在 ANSI 兼容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下无效。
