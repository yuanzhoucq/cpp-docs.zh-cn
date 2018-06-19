---
title: 表达式计算器错误 CXX0064 |Microsoft 文档
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
ms.openlocfilehash: 7964eac628fa89695d1757cff8b7b329fd7fe713
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302131"
---
# <a name="expression-evaluator-error-cxx0064"></a>表达式计算器错误 CXX0064
无法在绑定的虚拟成员函数上设置断点  
  
 如在通过指向对象的指针的虚拟成员函数上设置了断点：  
  
```  
pClass->vfunc( int );  
```  
  
 可以通过输入类，如在虚函数上设置断点：  
  
```  
Class::vfunc( int );  
```  
  
 此错误是与 CAN0064 相同。