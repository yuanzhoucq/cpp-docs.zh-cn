---
title: 编译器错误 C2427 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2427
dev_langs:
- C++
helpviewer_keywords:
- C2427
ms.assetid: a7d421af-6180-40b4-b7a6-9f3bc7dfaaf9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 27d18dff26d98adb0dada58271c4ec20fde73755
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104785"
---
# <a name="compiler-error-c2427"></a>编译器错误 C2427

class： 不能在此作用域中定义类

尝试定义嵌套的类，但嵌套的类是基类，不是最包含类的成员。

下面的示例生成 C2427:

```
// C2427.cpp
// compile with: /c
template <class T>
struct S {
   struct Inner;
};

struct Y : S<int> {};

struct Y::Inner {};   // C2427

// OK
template<typename T>
struct S<T>::Inner {};
```