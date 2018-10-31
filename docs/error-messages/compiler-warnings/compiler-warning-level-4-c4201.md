---
title: 编译器警告（等级 4）C4201
ms.date: 11/04/2016
f1_keywords:
- C4201
helpviewer_keywords:
- C4201
ms.assetid: 6156f508-9393-4d77-9e73-1ec3e1c32d0d
ms.openlocfilehash: c7c10273e06ec35528dbd9d51c02bb844d275638
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445794"
---
# <a name="compiler-warning-level-4-c4201"></a>编译器警告（等级 4）C4201

使用了非标准扩展： 无名称结构/联合

在 Microsoft 扩展 (/Ze) 中，可以指定而无需声明符的结构，为另一个结构或联合的成员。 这些结构生成 ANSI 兼容性错误 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。

## <a name="example"></a>示例

```
// C4201.cpp
// compile with: /W4
struct S
{
   float y;
   struct
   {
      int a, b, c;  // C4201
   };
} *p_s;

int main()
{
}
```