---
title: 编译器错误 C3640 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3640
dev_langs:
- C++
helpviewer_keywords:
- C3640
ms.assetid: fcc56894-0f98-48af-8561-3bf7c7b2b93f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f032f96d4e7af48ad98a75f2bf62058121f135d5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109192"
---
# <a name="compiler-error-c3640"></a>编译器错误 C3640

member： 必须定义局部类的一个引用或虚拟成员函数

编译器需要定义某些功能。

下面的示例生成 C3640:

```
// C3640.cpp
void f()
{
   struct S
   {
      virtual void f1();   // C3640
      // Try the following line instead:
      // virtual void f1(){}
   };
}
```