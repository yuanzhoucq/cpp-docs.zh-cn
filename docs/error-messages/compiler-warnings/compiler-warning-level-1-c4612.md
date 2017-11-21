---
title: "编译器警告 （等级 1） C4612 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4612
dev_langs: C++
helpviewer_keywords: C4612
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1a2d5ddc76271df594c2bd5b2ae1707933510338
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4612"></a>编译器警告（等级 1）C4612
包含文件名中有错误  
  
 当文件名不正确或缺失时，此警告与 **#pragma include_alias** 一起出现。  
  
 自变量**#pragma include_alias**语句可以使用引号 (**"***filename***"**) 或尖括号形式 (**\<**  *filename***>**)，但两者必须使用相同的形式。  
  
## <a name="example"></a>示例  
  
```  
// C4612.cpp  
// compile with: /W1 /LD  
#pragma include_alias("StandardIO", <stdio.h>) // C4612  
```