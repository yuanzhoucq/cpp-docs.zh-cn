---
title: 编译器错误 C3496
ms.date: 11/04/2016
f1_keywords:
- C3496
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
ms.openlocfilehash: 993d391f28a59afc8926748f2e6f34ab441657dc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228851"
---
# <a name="compiler-error-c3496"></a>编译器错误 C3496

“this”始终按值捕获: 已忽略“&”

不能 **`this`** 按引用捕获指针。

### <a name="to-correct-this-error"></a>更正此错误

- **`this`** 按值捕获指针。

## <a name="example"></a>示例

下面的示例生成 C3496，因为 **`this`** lambda 表达式的捕获列表中出现了对指针的引用：

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
