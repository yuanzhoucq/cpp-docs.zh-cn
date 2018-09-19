---
title: 编译器错误 C3222 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3222
dev_langs:
- C++
helpviewer_keywords:
- C3222
ms.assetid: 5624bde8-2fd0-4b8b-92ce-5dfbaf91cf93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 30231f74b379cd9d69806fbd4b49ba0cb55ad871
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048313"
---
# <a name="compiler-error-c3222"></a>编译器错误 C3222

“parameter”: 无法为托管或 WinRT 类型或泛型函数的成员函数声明默认自变量

不允许声明具有默认自变量的方法参数。 方法的重载形式是一种用于解决此问题的方式。 也就是说，定义具有相同名称但不带参数的方法，然后在方法体中初始化变量。

以下示例生成 C3222：

```
// C3222_2.cpp
// compile with: /clr
public ref class G {
   void f( int n = 0 );   // C3222
};
```
