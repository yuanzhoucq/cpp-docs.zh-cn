---
title: 编译器错误 C3495 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3495
dev_langs:
- C++
helpviewer_keywords:
- C3495
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dda1e2f2699969ad0bc446d9f79a0004e043998d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067384"
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


