---
title: "表达式计算器错误 CXX0064 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- CXX0064
dev_langs:
- C++
helpviewer_keywords:
- CAN0064
- CXX0064
ms.assetid: aa509e71-0616-41ca-a94e-6c376b041e57
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2edeb05e39c6d2e70cb2c9dde562a89e85921301
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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