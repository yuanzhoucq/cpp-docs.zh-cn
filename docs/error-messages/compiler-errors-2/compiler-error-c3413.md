---
title: 编译器错误 C3413 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3413
dev_langs:
- C++
helpviewer_keywords:
- C3413
ms.assetid: de6c9b05-c373-4bd8-8cb0-12c2cd2e5674
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c3ee8a8fd96b6fe5ed675f5e82a196d0ddb2cb3f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053279"
---
# <a name="compiler-error-c3413"></a>编译器错误 C3413

“name”：显式实例化无效

编译器检测到格式不正确的显式实例化。

下面的示例生成 C3413：

```
// C3413.cpp
template
class MyClass {};   // C3413
```

可能的解决方法：

```
// C3413b.cpp
// compile with: /c
template <class T>
class MyClass {};

template <>
class MyClass<int> {};
```