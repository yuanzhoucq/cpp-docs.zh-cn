---
title: 编译器错误 C3481
ms.date: 11/04/2016
f1_keywords:
- C3481
helpviewer_keywords:
- C3481
ms.assetid: 5d09375a-5ed3-4b61-86ed-45e91fd734c7
ms.openlocfilehash: eff7c7a4f39524aa1d894b7b4590aa809714aae6
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041197"
---
# <a name="compiler-error-c3481"></a>编译器错误 C3481

“var”：未找到 lambda 捕获变量

编译器未找到传递给 lambda 表达式捕获列表的变量的定义。

### <a name="to-correct-this-error"></a>更正此错误

- 从 lambda 表达式的捕获列表中删除该变量。

## <a name="example"></a>示例

下面的示例由于未定义变量 `n` 而生成 C3481：

```
// C3481.cpp

int main()
{
   [n] {}(); // C3481
}
```

## <a name="see-also"></a>请参阅

[Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)