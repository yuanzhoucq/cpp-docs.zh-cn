---
title: "编译器错误 C2483 |Microsoft 文档"
ms.custom: 
ms.date: 09/15/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2483
dev_langs:
- C++
helpviewer_keywords:
- C2483
ms.assetid: 5762b325-914b-442d-a604-e4617ba04038
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5f7f9f30724c02d44e054bf16ff1460370c30e06
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2483"></a>编译器错误 C2483

>*标识符*： 用构造函数或析构函数的对象不能声明为线程

此错误消息是在 Visual Studio 2015 及更高版本中过时。 在早期版本中，变量声明与`thread`不能用一个构造函数或其他需要运行时计算的表达式初始化属性。 初始化所需的静态表达式`thread`数据。

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