---
title: 编译器错误 C3496
ms.date: 11/04/2016
f1_keywords:
- C3496
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
ms.openlocfilehash: b9542f1904c6797a77c88c88a37aff9348364268
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738175"
---
# <a name="compiler-error-c3496"></a>编译器错误 C3496

“this”始终按值捕获: 已忽略“&”

不能按引用捕获 `this` 指针。

### <a name="to-correct-this-error"></a>更正此错误

- 按值捕获 `this` 指针。

## <a name="example"></a>示例

下面的示例将生成 C3496，因为 lambda 表达式的捕获列表中出现了对 `this` 指针的引用：

```cpp
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

## <a name="see-also"></a>另请参阅

[Lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)
