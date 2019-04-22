---
title: 编译器错误 C3496
ms.date: 11/04/2016
f1_keywords:
- C3496
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
ms.openlocfilehash: 025498f3fe244916cd0a06e36feee6fdb532acc6
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026683"
---
# <a name="compiler-error-c3496"></a>编译器错误 C3496

“this”始终按值捕获: 已忽略“&”

不能按引用捕获 `this` 指针。

### <a name="to-correct-this-error"></a>更正此错误

- 按值捕获 `this` 指针。

## <a name="example"></a>示例

下面的示例将生成 C3496，因为 lambda 表达式的捕获列表中出现了对 `this` 指针的引用：

```
// C3496.cpp
// compile with: /c

class C
{
   void f()
   {
      [&this] {}(); // C3496
   }
};
```

## <a name="see-also"></a>请参阅

[Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)