---
title: 编译器错误 C3537
ms.date: 11/04/2016
f1_keywords:
- C3537
helpviewer_keywords:
- C3537
ms.assetid: f537ebd1-4fb0-4e09-a453-4f38db2c6881
ms.openlocfilehash: 663ef761d6c52aeb4c3cc9ce109079c647904e36
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87197548"
---
# <a name="compiler-error-c3537"></a>编译器错误 C3537

"type"：不能强制转换为包含 "auto" 的类型

不能将变量强制转换为指定的类型，因为该类型包含 **`auto`** 关键字并且默认[/zc： auto](../../build/reference/zc-auto-deduce-variable-type.md)编译器选项有效。

## <a name="example"></a>示例

下面的代码将生成 C3537，因为这些变量将强制转换为包含关键字的类型 **`auto`** 。

```cpp
// C3537.cpp
// Compile with /Zc:auto
int main()
{
   int value = 123;
   auto(value);                        // C3537
   (auto)value;                        // C3537
   auto x1 = auto(value);              // C3537
   auto x2 = (auto)value;              // C3537
   auto x3 = static_cast<auto>(value); // C3537
   return 0;
}
```

## <a name="see-also"></a>请参阅

[auto 关键字](../../cpp/auto-keyword.md)
