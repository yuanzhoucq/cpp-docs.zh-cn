---
title: "编译器错误 C2624 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2624
dev_langs: C++
helpviewer_keywords: C2624
ms.assetid: 32f2ec15-a7cd-4049-a64b-131746d3152b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c70165fc0d57d753dadd2bed207a00e3dd3498aa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2624"></a>编译器错误 C2624
局部类不能用于声明变量的外部  
  
 局部类或结构不能用于声明`extern`变量。  
  
 下面的示例生成 C2624:  
  
```  
// C2624.cpp  
int main() {  
   struct C {};  
   extern C ac;   // C2624  
}  
```