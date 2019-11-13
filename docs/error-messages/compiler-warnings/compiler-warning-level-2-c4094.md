---
title: 编译器警告（等级2） C4094
ms.date: 11/04/2016
f1_keywords:
- C4094
helpviewer_keywords:
- C4094
ms.assetid: e68929fb-3a1c-4be7-920b-d5f79f534f99
ms.openlocfilehash: c293522e5d60d0edb4cc2da289e0ece71f89329f
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052204"
---
# <a name="compiler-warning-level-2-c4094"></a>编译器警告（等级2） C4094

未标记的 "token" 未声明符号

编译器检测到使用了未标记的结构、联合或类的空声明。 声明将被忽略。

## <a name="example"></a>示例

```cpp
// C4094.cpp
// compile with: /W2
struct
{
};   // C4094

int main()
{
}
```

此条件在 ANSI 兼容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下生成错误。