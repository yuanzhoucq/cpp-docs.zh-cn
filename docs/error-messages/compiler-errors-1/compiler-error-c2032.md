---
title: 编译器错误 C2032 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2032
dev_langs:
- C++
helpviewer_keywords:
- C2032
ms.assetid: 625d7c83-70b6-42c2-a558-81fbc0026324
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ab02ca695ec94f25054e3490232b782a46a53a4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064004"
---
# <a name="compiler-error-c2032"></a>编译器错误 C2032

identifier： 函数不能是成员的结构/联合 structorunion

结构或联合有一个 c + + 中，但不是在 C 中允许的成员函数若要解决此错误，请编译为 c + + 程序或删除成员函数。

下面的示例生成 C2032:

```
// C2032.c
struct z {
   int i;
   void func();   // C2032
};
```

可能的解决方法：

```
// C2032b.c
// compile with: /c
struct z {
   int i;
};
```