---
title: 编译器警告（等级 4）C4207
ms.date: 11/04/2016
f1_keywords:
- C4207
helpviewer_keywords:
- C4207
ms.assetid: f4e09e3e-ac87-4489-8e3f-c8f76b82e721
ms.openlocfilehash: 1ff669512f85dfed9bab307c2986e7858285461d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161381"
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
