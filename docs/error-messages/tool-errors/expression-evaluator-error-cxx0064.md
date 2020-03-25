---
title: 表达式计算器错误 CXX0064
ms.date: 11/04/2016
f1_keywords:
- CXX0064
helpviewer_keywords:
- CAN0064
- CXX0064
ms.assetid: aa509e71-0616-41ca-a94e-6c376b041e57
ms.openlocfilehash: f763754299ed9257fb909b49a7a19c6f3ad58681
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80184458"
---
# <a name="expression-evaluator-error-cxx0064"></a>表达式计算器错误 CXX0064

无法在绑定虚拟成员函数上设置断点

通过指向对象的指针对虚拟成员函数设置了断点，例如：

```
pClass->vfunc( int );
```

可以通过输入类在虚函数上设置断点，例如：

```
Class::vfunc( int );
```

此错误与 CAN0064 相同。
