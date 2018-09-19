---
title: 编译器错误 C2790 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2790
dev_langs:
- C++
helpviewer_keywords:
- C2790
ms.assetid: 38d4fce1-ba00-413d-8bc1-e8aa43d7bc1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc2c6b238fab7e42c0754e613b62756a86a5bb31
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069568"
---
# <a name="compiler-error-c2790"></a>编译器错误 C2790

super： 此关键字仅在类成员函数的主体内部使用

如果用户曾经试图使用关键字，则出现此错误消息[super](../../cpp/super.md)成员函数的上下文之外。

下面的示例生成 C2790:

```
// C2790.cpp
void f() {
   __super::g();   // C2790
}
```