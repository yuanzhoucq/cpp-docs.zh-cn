---
title: "编译器错误 C2458 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2458
dev_langs: C++
helpviewer_keywords: C2458
ms.assetid: ed21901f-1067-42f5-b275-19b480decf5c
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 511d6685ff6447793baa14468f6414fec99a3772
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2458"></a>编译器错误 C2458
identifier： 重定义内定义  
  
 类、 结构、 联合或枚举是在其自己的声明中重新定义。  
  
 下面的示例生成 C2458:  
  
```  
// C2458.cpp  
class C {  
   enum i { C };   // C2458  
};  
```