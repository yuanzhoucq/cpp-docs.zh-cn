---
title: 编译器错误 C2377 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2377
dev_langs:
- C++
helpviewer_keywords:
- C2377
ms.assetid: f7660965-bf4c-4cd9-8307-1bd7016678a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f3813642503013ecd2ad3be4c01d55f12c837ba
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087028"
---
# <a name="compiler-error-c2377"></a>编译器错误 C2377

“identifier”：重定义；typedef 不能由任何其他符号重载

`typedef` 标识符被重新定义。

以下示例生成 C2377：

```
// C2377.cpp
// compile with: /c
typedef int i;
int i;   // C2377
int j;   // OK
```