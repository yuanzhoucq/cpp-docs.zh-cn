---
title: "编译器警告 （等级 3） C4310 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4310
dev_langs: C++
helpviewer_keywords: C4310
ms.assetid: cba3eca1-f1ed-499c-9243-337446bdbdd8
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8e831459aaf2161d83a62cd1241673780293c02d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4310"></a>编译器警告（等级 3）C4310
强制转换截断常量值  
  
 常量值被强制转换为更小的类型。 编译器将执行转换，将截断数据。 下面的示例生成 C4310:  
  
```  
// C4310.cpp  
// compile with: /W4  
int main() {  
   long int a;  
   a = (char) 128;   // C4310, use value 0-127 to resolve  
}  
```