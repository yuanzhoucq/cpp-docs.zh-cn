---
title: 编译器错误 C2483 |Microsoft Docs
ms.custom: ''
ms.date: 09/15/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2483
dev_langs:
- C++
helpviewer_keywords:
- C2483
ms.assetid: 5762b325-914b-442d-a604-e4617ba04038
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be2a2caef9e1252bf1ab36253a7f5f715b94d5a3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031608"
---
# <a name="compiler-error-c2483"></a>编译器错误 C2483

>'*标识符*： 用构造函数或析构函数的对象不能声明为线程

此错误消息是在 Visual Studio 2015 及更高版本中已过时。 在早期版本中，变量声明与`thread`属性不能使用构造函数或其他需要运行时计算的表达式进行初始化。 初始化所需的静态表达式`thread`数据。

## <a name="example"></a>示例

下面的示例生成 C2483 Visual Studio 2013 和早期版本中。

```cpp
// C2483.cpp
// compile with: /c
__declspec(thread) struct A {
   A(){}
   ~A(){}
} aa;   // C2483 error

__declspec(thread) struct B {} b;   // OK
```

## <a name="see-also"></a>请参阅

[thread](../../cpp/thread.md)