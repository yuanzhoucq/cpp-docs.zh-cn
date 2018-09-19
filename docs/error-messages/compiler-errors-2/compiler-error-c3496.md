---
title: 编译器错误 C3496 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3496
dev_langs:
- C++
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ec4602e6a0061f5eb750ab29587209a6c97985d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062288"
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