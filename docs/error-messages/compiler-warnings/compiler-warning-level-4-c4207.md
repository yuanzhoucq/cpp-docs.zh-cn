---
title: 编译器警告（等级 4）C4207
ms.date: 11/04/2016
f1_keywords:
- C4207
helpviewer_keywords:
- C4207
ms.assetid: f4e09e3e-ac87-4489-8e3f-c8f76b82e721
ms.openlocfilehash: 44f49705bf197d7a42b80e50983e47a4c0ce7bed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50541113"
---
# <a name="compiler-warning-level-4-c4207"></a>编译器警告（等级 4）C4207

使用了非标准扩展： 扩展初始值设定项窗体

使用 Microsoft 扩展 (/Ze)，您可以初始化数组未确定大小的`char`使用大括号内的字符串。

## <a name="example"></a>示例

```
// C4207.c
// compile with: /W4
char c[] = { 'a', 'b', "cdefg" }; // C4207

int main()
{
}
```

此类初始化将是无效 ANSI 兼容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。