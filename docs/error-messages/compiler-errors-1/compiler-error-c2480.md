---
title: 编译器错误 C2480
ms.date: 11/04/2016
f1_keywords:
- C2480
helpviewer_keywords:
- C2480
ms.assetid: 1a58d1c2-971b-4084-96fa-f94aa51c02f1
ms.openlocfilehash: 3e495a8019405a558511637467133877dae1183e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743518"
---
# <a name="compiler-error-c2480"></a>编译器错误 C2480

"identifier"： "thread" 只对静态范围的数据项有效

不能将 `thread` 特性与自动变量、非静态数据成员、函数参数或函数声明或定义一起使用。

仅将 `thread` 特性用于全局变量、静态数据成员和局部静态变量。

下面的示例生成 C2480：

```cpp
// C2480.cpp
// compile with: /c
__declspec( thread ) void func();   // C2480
__declspec( thread ) static int i;   // OK
```
