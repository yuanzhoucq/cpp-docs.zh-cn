---
title: 编译器错误 C2838 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2838
dev_langs:
- C++
helpviewer_keywords:
- C2838
ms.assetid: 176b2ad6-7a84-4019-b97e-328866054457
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5607df86a44174536f58242c5c0a98f7fe5e7dc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045271"
---
# <a name="compiler-error-c2838"></a>编译器错误 C2838

member： 成员声明中的非法限定的名

类、 结构或联合使用完全限定的名称重新声明另一个类、 结构或联合的成员。

下面的示例生成 C2838:

```
// C2838.cpp
// compile with: /c
class Bellini {
public:
    void Norma();
};

class Bottesini {
   Bellini::Norma();  // C2838
};
```