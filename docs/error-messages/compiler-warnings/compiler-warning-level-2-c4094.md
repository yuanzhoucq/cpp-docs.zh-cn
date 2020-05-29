---
title: 编译器警告（等级2） C4094
ms.date: 11/04/2016
f1_keywords:
- C4094
helpviewer_keywords:
- C4094
ms.assetid: e68929fb-3a1c-4be7-920b-d5f79f534f99
ms.openlocfilehash: c90ad202e193f21955d396dd2aff6b39d3a968c7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174331"
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
