---
title: 编译器错误 C3483
ms.date: 11/04/2016
f1_keywords:
- C3483
helpviewer_keywords:
- C3483
ms.assetid: 18b3a2c5-dfc9-4661-9653-08a5798474cf
ms.openlocfilehash: acbe89b5183d0991fb8d4a571a9595d6f6bafc6c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62381342"
---
# <a name="compiler-error-c3483"></a>编译器错误 C3483

“var”已经是 lambda 捕获列表的一部分

你不止一次向 lambda 表达式的捕获列表传递了相同的变量。

### <a name="to-correct-this-error"></a>更正此错误

- 从捕获列表中删除变量的所有其他实例。

## <a name="example"></a>示例

下面的示例将生成 C3483，因为变量 `n` 在 lambda 表达式的捕获列表中出现了多次。

```
// C3483.cpp

int main()
{
   int m = 6, n = 5;
   [m,n,n] { return n + m; }(); // C3483
}
```

## <a name="see-also"></a>请参阅

[Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)