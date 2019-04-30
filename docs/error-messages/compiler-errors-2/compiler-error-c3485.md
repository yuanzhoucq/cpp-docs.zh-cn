---
title: 编译器错误 C3485
ms.date: 11/04/2016
f1_keywords:
- C3485
helpviewer_keywords:
- C3485
ms.assetid: d67536f9-67a1-4ad9-9a94-d8bbbca3d0dc
ms.openlocfilehash: 2fcaecd6be35e2ae6822133930b48b6bbf02aafe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62381133"
---
# <a name="compiler-error-c3485"></a>编译器错误 C3485

lambda 定义不能包含任何 cv 限定符

不能使用 `const` 或 `volatile` 限定符作为 lambda 表达式定义的一部分。

### <a name="to-correct-this-error"></a>更正此错误

- 从 lambda 表达式定义中删除 `const` 或 `volatile` 限定符。

## <a name="example"></a>示例

以下示例生成 C3485，因为它使用 `const` 限定符作为 lambda 表达式定义的一部分：

```
// C3485.cpp

int main()
{
   auto x = []() const mutable {}; // C3485
}
```

## <a name="see-also"></a>请参阅

[Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)