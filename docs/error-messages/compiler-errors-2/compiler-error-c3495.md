---
title: 编译器错误 C3495
ms.date: 11/04/2016
f1_keywords:
- C3495
helpviewer_keywords:
- C3495
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
ms.openlocfilehash: 1a61d4f2472ef6da8aedcf8a8ef90b70de47d8af
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738266"
---
# <a name="compiler-error-c3495"></a>编译器错误 C3495

“var”：lambda 捕获必须有自动存储持续时间

不能捕获没有自动存储持续时间的变量，如标记为 `static` 或 `extern`的变量。

### <a name="to-correct-this-error"></a>更正此错误

- 不要将 `static` 或 `extern` 变量传递到 lambda 表达式的捕获列表。

## <a name="example"></a>示例

下面的示例将生成 C3495，因为 lambda 表达式的捕获列表中出现了 `static` 变量 `n` ：

```cpp
// C3495.cpp

int main()
{
   static int n = 66;
   [&n]() { return n; }(); // C3495
}
```

## <a name="see-also"></a>另请参阅

[Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)

