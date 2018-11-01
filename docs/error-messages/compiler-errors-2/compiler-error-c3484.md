---
title: 编译器错误 C3484
ms.date: 11/04/2016
f1_keywords:
- C3484
helpviewer_keywords:
- C3484
ms.assetid: 2fe847fa-f6ee-4978-bc1d-b6dc6ae906ac
ms.openlocfilehash: fd8909b664f739afa1ab1208be0984b8f410154d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468620"
---
# <a name="compiler-error-c3484"></a>编译器错误 C3484

返回类型前应为“->”

你必须在 lambda 表达式的返回类型前提供 `->`。

### <a name="to-correct-this-error"></a>更正此错误

- 在返回类型前提供 `->` 。

## <a name="example"></a>示例

下面的示例生成 C3484：

```
// C3484a.cpp

int main()
{
   return []() . int { return 42; }(); // C3484
}
```

## <a name="example"></a>示例

下面的示例通过在 lambda 表达式的返回类型之前提供 `->` 来解决 C3484：

```
// C3484b.cpp

int main()
{
   return []() -> int { return 42; }();
}
```

## <a name="see-also"></a>请参阅

[Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)