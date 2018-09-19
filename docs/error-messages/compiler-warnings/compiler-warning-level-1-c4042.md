---
title: 编译器警告 （等级 1） C4042 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4042
dev_langs:
- C++
helpviewer_keywords:
- C4042
ms.assetid: e4bd861b-1194-426b-bf79-68c5b021eb0a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5bef2071cf31123b5b172df2651c0d6a6d87d4fc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067463"
---
# <a name="compiler-warning-level-1-c4042"></a>编译器警告 （等级 1） C4042

identifier： 具有错误的存储类

指定的存储类不能用于在此上下文中此标识符。 编译器将改为使用默认的存储类：

- `extern`如果*标识符*是一个函数。

- **自动**，如果*标识符*是形参或局部变量。

- 没有存储类，如果*标识符*是全局变量。

可以通过指定存储类而不导致该警告**注册**参数声明中。

下面的示例生成 C4042

```
// C4042.cpp
// compile with: /W1 /LD
int func2( __declspec( thread ) int tls_i )    // C4042
// try the following line instead
// int func2( int tls_i )
{
   return tls_i;
}
```