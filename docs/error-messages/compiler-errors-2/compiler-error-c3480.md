---
title: 编译器错误 C3480
ms.date: 11/04/2016
f1_keywords:
- C3480
helpviewer_keywords:
- C3480
ms.assetid: 7b2e055a-9604-4d13-861b-b38bda1a6940
ms.openlocfilehash: 255fb12d587a94aac798814736f0b26770f608b0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760473"
---
# <a name="compiler-error-c3480"></a>编译器错误 C3480

“var”：lambda 捕获变量必须来自封闭函数范围

Lambda 捕获变量不是来自封闭函数范围。

### <a name="to-correct-this-error"></a>更正此错误

- 从 lambda 表达式的捕获列表中删除该变量。

## <a name="example"></a>示例

下面的示例将生成 C3480，因为变量 `global` 不是来自封闭函数范围：

```cpp
// C3480a.cpp

int global = 0;
int main()
{
   [&global] { global = 5; }(); // C3480
}
```

## <a name="example"></a>示例

下面的示例通过从 lambda 表达式的捕获列表中删除变量 `global` 来解决 C3480：

```cpp
// C3480b.cpp

int global = 0;
int main()
{
   [] { global = 5; }();
}
```

## <a name="see-also"></a>另请参阅

[Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)
