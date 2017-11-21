---
title: "编译器错误 C2733 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2733
dev_langs: C++
helpviewer_keywords: C2733
ms.assetid: 67f83561-c633-407c-a2ee-f9fd16e165bf
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 22643ad7b1e801f2e4b9ee663c73f0d8fb97562d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2733"></a>编译器错误 C2733
第二个 C 链接的重载函数 function 不允许  
  
 使用 C 链接声明多个重载的函数。 使用 C 链接时，只有一种形式的指定可以是函数的外部的。 重载的函数具有相同的未修饰的名称，因为它们不能用于 C 程序。  
  
 下面的示例生成 C2733:  
  
```  
// C2733.cpp  
extern "C" {  
   void F1(int);  
}  
  
extern "C" {  
   void F1();   // C2733  
   // try the following line instead  
   // void F2();  
}  
```