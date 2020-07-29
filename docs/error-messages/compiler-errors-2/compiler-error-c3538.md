---
title: 编译器错误 C3538
ms.date: 11/04/2016
f1_keywords:
- C3538
helpviewer_keywords:
- C3538
ms.assetid: ef3698a5-7356-4c62-b9af-5d3a4baed958
ms.openlocfilehash: 290faa1a227920cd46f32a4adf0dd6a6f3687c6d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233361"
---
# <a name="compiler-error-c3538"></a>编译器错误 C3538

在声明符列表中，“auto”必须始终推导为同一类型

声明列表中的所有已声明变量不解析为同一类型。

### <a name="to-correct-this-error"></a>更正此错误

1. 确保 **`auto`** 列表中的所有声明都推导为同一类型。

## <a name="example"></a>示例

下面的语句生成 C3538。 每个语句声明多个变量，但关键字的每个使用都 **`auto`** 不能推导为同一类型。

```cpp
// C3538.cpp
// Compile with /Zc:auto
// C3538 expected
int main()
{
// Variable x1 is a pointer to char, but y1 is a double.
   auto * x1 = "a", y1 = 3.14;
// Variable c is a char and c1 is char*, but c2, and c3 are pointers to pointers.
   auto c = 'a', *c1 = &c, * c2 = &c1, * c3 = &c2;
// Variable x2 is an int, but y2 is a double and z is a char.
   auto x2(1), y2(0.0), z = 'a';
// Variable a is a pointer to int, but b is a pointer to double.
   auto *a = new auto(1), *b = new auto(2.0);
   return 0;
}
```

## <a name="see-also"></a>请参阅

[auto 关键字](../../cpp/auto-keyword.md)
