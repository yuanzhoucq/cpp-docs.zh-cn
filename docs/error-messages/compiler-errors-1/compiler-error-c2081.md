---
title: 编译器错误 C2081 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2081
dev_langs:
- C++
helpviewer_keywords:
- C2081
ms.assetid: 7db9892d-364d-4178-a49d-f8398ece09a0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 48f2cdecaea38beed14735bb3f94c8422a28c747
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030451"
---
# <a name="compiler-error-c2081"></a>编译器错误 C2081

identifier： 非法的形参列表中的名称

标识符导致语法错误。

可以通过使用旧样式的形参列表导致此错误。 形参列表中，必须指定的正式参数的类型。

下面的示例生成 C2081:

```
// C2081.c
void func( int i, j ) {}  // C2081, no type specified for j
```

可能的解决方法：

```
// C2081b.c
// compile with: /c
void func( int i, int j ) {}
```