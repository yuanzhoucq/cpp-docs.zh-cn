---
title: 编译器警告 （等级 1） C4172 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4172
dev_langs:
- C++
helpviewer_keywords:
- C4172
ms.assetid: a8d2bf65-d8b1-4fe3-8340-a223d7e7fde6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 56f606b48fb060472dd67d34800c06946bc41712
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043503"
---
# <a name="compiler-warning-level-1-c4172"></a>编译器警告 （等级 1） C4172

返回地址的本地变量或临时

一个函数返回的本地变量或临时对象的地址。 本地变量和临时对象会被销毁时某个函数返回，因此返回的地址无效。

重新设计函数，以便它不返回本地对象的地址。

下面的示例生成 C4172:

```
// C4172.cpp
// compile with: /W1 /LD
float f = 10;

const double& bar() {
// try the following line instead
// const float& bar() {
   return f;   // C4172
}
```