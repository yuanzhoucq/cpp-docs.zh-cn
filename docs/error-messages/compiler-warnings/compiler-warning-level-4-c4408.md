---
title: "编译器警告 （等级 4） C4408 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4408
dev_langs: C++
helpviewer_keywords: C4408
ms.assetid: 8488a186-ed1d-425c-aaeb-c72472c1da68
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4c1d585283428536e0f5faabad25e3a84cb2a6f7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4408"></a>编译器警告（等级 4）C4408
anonymousstruct 或联合不声明任何数据成员  
  
 匿名结构或联合必须具有至少一个数据成员。  
  
 以下示例生成 C4408：  
  
```  
// C4408.cpp  
// compile with: /W4 /LD  
static union  
{  
   // int i;  
};  
// a named union can have no data members  
// } MyUnion;  
```