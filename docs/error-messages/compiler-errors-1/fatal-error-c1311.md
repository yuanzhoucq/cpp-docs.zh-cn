---
title: "错误 C1311 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1311
dev_langs:
- C++
helpviewer_keywords:
- C1311
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 9aeb63e041ddfe26a8fc47afc838f2f5c3ce35d6
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="fatal-error-c1311"></a>错误 C1311
COFF 格式无法以静态方式初始化 var 具有数字字节的地址  
  
 在编译时不知道其值的地址不能以静态方式分配给其类型具有不超过四个字节的存储变量。  
  
 上，则代码可能会发生此错误有效的 c + +。  
  
 以下示例显示了可能导致 C1311 的一种情况。  
  
```  
char c = (char)"Hello, world";   // C1311  
char *d = (char*)"Hello, world";   // OK  
```
