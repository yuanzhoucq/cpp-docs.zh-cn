---
title: 表达式计算器错误 CXX0064 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0064
dev_langs:
- C++
helpviewer_keywords:
- CAN0064
- CXX0064
ms.assetid: aa509e71-0616-41ca-a94e-6c376b041e57
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b16133484af5a2225f79c5d293a2c8edd948bdb2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025888"
---
# <a name="expression-evaluator-error-cxx0064"></a>表达式计算器错误 CXX0064

不能在绑定的虚拟成员函数上设置断点

如通过指向对象的指针的虚拟成员函数上设置了断点：

```
pClass->vfunc( int );
```

可以通过输入类，如在虚函数上设置断点：

```
Class::vfunc( int );
```

此错误是与 CAN0064 相同。