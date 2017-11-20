---
title: "编译器错误 C2657 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2657
dev_langs: C++
helpviewer_keywords: C2657
ms.assetid: f7cf29a9-684a-4605-9469-ecfee9ba4b03
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2e0e06104458961297a4d0a3de8b7cda756d16ab
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2657"></a>编译器错误 C2657
类:: * 语句的起始处找到 （是否忘记指定类型？）  
  
 行开头的指针到成员标识符。  
  
 到成员，指针的声明中缺少类型说明符可以导致此错误。  
  
 下面的示例生成 C2657:  
  
```  
// C2657.cpp  
class C {};  
int main() {  
   C::* pmc1;        // C2657  
   int C::* pmc2;   // OK  
}  
```