---
title: 编译器错误 C2500 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2500
dev_langs:
- C++
helpviewer_keywords:
- C2500
ms.assetid: 6bff8161-dc9a-48ca-91f1-fd2eefdbbc93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b7e24ca520796b63171fe63c2bf841fe8776845
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026665"
---
# <a name="compiler-error-c2500"></a>编译器错误 C2500

identifier1: identifier2 已经是直接基类

类或结构的基类列表中多次出现。

直接基是基列表中所述。 间接基是基类的基列表中的类之一。

类不能多次指定为直接基类。 可以多次作为间接基类使用类。

下面的示例生成 C2500:

```
// C2500.cpp
// compile with: /c
class A {};
class B : public A, public A {};    // C2500

// OK
class C : public A {};
class D : public A {};
class E : public C, public D {};
```