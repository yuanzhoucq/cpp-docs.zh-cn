---
title: 编译器错误 C3495
ms.date: 11/04/2016
f1_keywords:
- C3495
helpviewer_keywords:
- C3495
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
ms.openlocfilehash: a67d4d859e3a9dd2241f14a476492df0fd3e6b8d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223416"
---
# <a name="compiler-error-c3495"></a>编译器错误 C3495

“var”：lambda 捕获必须有自动存储持续时间

不能捕获没有自动存储持续时间的变量，如标记为或的变量 **`static`** **`extern`** 。

### <a name="to-correct-this-error"></a>更正此错误

- 不要将 **`static`** 或变量传递 **`extern`** 到 lambda 表达式的捕获列表。

## <a name="example"></a>示例

下面的示例生成 C3495，因为 **`static`** 变量 `n` 出现在 lambda 表达式的捕获列表中：

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
