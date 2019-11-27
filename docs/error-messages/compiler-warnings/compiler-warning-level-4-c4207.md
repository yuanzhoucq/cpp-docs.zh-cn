---
title: 编译器警告（等级 4）C4207
ms.date: 11/04/2016
f1_keywords:
- C4207
helpviewer_keywords:
- C4207
ms.assetid: f4e09e3e-ac87-4489-8e3f-c8f76b82e721
ms.openlocfilehash: bd18964f8969bc75967de435e2ca3099b12213e0
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541878"
---
# <a name="compiler-warning-level-4-c4207"></a>编译器警告（等级 4）C4207

使用了非标准扩展：扩展初始值设定项窗体

使用 Microsoft 扩展（/Ze），可以使用大括号内的字符串初始化 `char` 的成员列表数组数组。

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