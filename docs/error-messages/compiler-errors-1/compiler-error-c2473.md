---
title: "编译器错误 C2473 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2473
dev_langs: C++
helpviewer_keywords: C2473
ms.assetid: 6bb7dbf5-b198-490f-860e-fd64d0c2a284
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bbc3432383e39913ed3cd89b310b00706a26a589
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2473"></a>编译器错误 C2473
“identifier”: 看起来像函数定义，但却没有参数列表。  
  
 编译器检测到看似为函数、但没有参数列表的内容。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2473。  
  
```  
// C2473.cpp  
// compile with: /clr /c  
class A {  
   int i {}   // C2473  
};  
  
class B {  
   int i() {}   // OK  
};  
```