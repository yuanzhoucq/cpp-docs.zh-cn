---
title: 编译器错误 C2480
ms.date: 11/04/2016
f1_keywords:
- C2480
helpviewer_keywords:
- C2480
ms.assetid: 1a58d1c2-971b-4084-96fa-f94aa51c02f1
ms.openlocfilehash: 90016b65d4ddd58da3fb3c5ab6d81322dc0ef394
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187588"
---
# <a name="compiler-error-c2480"></a>编译器错误 C2480

identifier: thread 只是对静态作用域的数据项有效

不能使用`thread`使用自动变量、 非静态数据成员、 函数参数或函数声明或定义的属性。

使用`thread`属性，全局变量、 静态数据成员，并且仅本地静态变量。

下面的示例生成 C2480:

```
// C2480.cpp
// compile with: /c
__declspec( thread ) void func();   // C2480
__declspec( thread ) static int i;   // OK
```