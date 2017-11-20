---
title: "编译器警告 （等级 1） C4186 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4186
dev_langs: C++
helpviewer_keywords: C4186
ms.assetid: caf3f7d8-f305-426b-8d4e-2b96f5c269ea
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6d4286e834f4ee9ac644dfe28ed2d702cb894b5f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4186"></a>编译器警告（等级 1）C4186
\#导入特性 attribute 需要计数自变量;忽略  
  
 `#import` 特性的参数数量不正确。  
  
## <a name="example"></a>示例  
  
```  
// C4186.cpp  
// compile with: /W1 /c  
#import "stdole2.tlb" no_namespace("abc") rename("a","b","c")  // C4186  
```  
  
 `no_namespace` 特性不采用任何参数。 **rename** 特性仅采用两个参数。