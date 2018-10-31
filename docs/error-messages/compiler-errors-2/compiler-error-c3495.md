---
title: 编译器错误 C3495
ms.date: 11/04/2016
f1_keywords:
- C3495
helpviewer_keywords:
- C3495
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
ms.openlocfilehash: 81fcbb8102d5df8059aad00772b7ee0cc07c01d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452463"
---
# <a name="compiler-error-c3495"></a>编译器错误 C3495

“var”：lambda 捕获必须有自动存储持续时间

不能捕获没有自动存储持续时间的变量，如标记为 `static` 或 `extern`的变量。

### <a name="to-correct-this-error"></a>更正此错误

- 不要将 `static` 或 `extern` 变量传递到 lambda 表达式的捕获列表。

## <a name="example"></a>示例

下面的示例将生成 C3495，因为 lambda 表达式的捕获列表中出现了 `static` 变量 `n` ：

```
// C3495.cpp

int main()
{
   static int n = 66;
   [&n]() { return n; }(); // C3495
}
```

## <a name="see-also"></a>请参阅

[Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)

