---
title: 编译器错误 C2482 |Microsoft 文档
ms.custom: ''
ms.date: 09/15/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2482
dev_langs:
- C++
helpviewer_keywords:
- C2482
ms.assetid: 98c87da2-625c-4cc2-9bf7-78d15921e779
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2c4725dd357854db504272e5b8b9d88641b143d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2482"></a>编译器错误 C2482

>*标识符*： 不允许的线程数据的动态初始化

此错误消息是在 Visual Studio 2015 及更高版本中过时。 在早期版本中，变量声明使用`thread`不能用需要运行时计算的表达式初始化属性。 初始化所需的静态表达式`thread`数据。

## <a name="example"></a>示例

下面的示例生成 C2482 在 Visual Studio 2013 和早期版本：

```cpp
// C2482.cpp
// compile with: /c
#define Thread __declspec( thread )
Thread int tls_i = tls_i;   // C2482

int j = j;   // OK in C++; C error
Thread int tls_i = sizeof( tls_i );   // Okay in C and C++
```
