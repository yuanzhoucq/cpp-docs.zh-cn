---
title: "表达式计算器错误 CXX0064 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CXX0064
dev_langs: C++
helpviewer_keywords:
- CAN0064
- CXX0064
ms.assetid: aa509e71-0616-41ca-a94e-6c376b041e57
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ada57d8df67054fa6577b128a6be73921fbb7e81
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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