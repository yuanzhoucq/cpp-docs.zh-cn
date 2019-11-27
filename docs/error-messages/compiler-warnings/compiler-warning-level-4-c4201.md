---
title: 编译器警告（等级 4）C4201
ms.date: 11/04/2016
f1_keywords:
- C4201
helpviewer_keywords:
- C4201
ms.assetid: 6156f508-9393-4d77-9e73-1ec3e1c32d0d
ms.openlocfilehash: 1f029d7717f99e55a977ad9cb80dacbfa1485086
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541217"
---
# <a name="compiler-warning-level-4-c4201"></a>编译器警告（等级 4）C4201

使用了非标准扩展：无号结构/联合

在 Microsoft 扩展（/Ze）下，可以指定一个不包含声明符的结构作为另一个结构或联合的成员。 这些结构在 ANSI 兼容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下生成错误。

## <a name="example"></a>示例

```cpp
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