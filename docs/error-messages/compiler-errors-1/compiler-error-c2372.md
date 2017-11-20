---
title: "编译器错误 C2372 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2372
dev_langs: C++
helpviewer_keywords: C2372
ms.assetid: 406bea63-c8d3-4231-9d26-c70af6980840
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 334abb814d9a3bbadfb7c0c9060a333c9de880db
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2372"></a>编译器错误 C2372
identifier： 重定义;不同类型的间接寻址  
  
 使用不同的派生类型已定义标识符。  
  
 下面的示例生成 C2326:  
  
```  
// C2372.cpp  
// compile with: /c  
extern int *fp;  
extern int fp[];   // C2372  
extern int fp2[];   // OK  
```