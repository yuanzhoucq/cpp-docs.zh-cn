---
title: "编译器警告 （等级 1） C4530 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4530
dev_langs: C++
helpviewer_keywords: C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cd91b0c46e5243a223b3b8ab8cdfc9a03cd64cb2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4530"></a>编译器警告（等级 1）C4530
C + + 异常处理程序使用，但展开语义未启用。 指定 /EHsc  
  
 已使用 c + + 异常处理，但[/EHsc](../../build/reference/eh-exception-handling-model.md)未选中。  
  
 当尚未启用 /EHsc 选项时，将不销毁具有自动存储在框架中，执行引发函数和函数与捕捉引发，之间的对象。 但是，在创建具有自动存储对象**重**或**捕获**块将被销毁。  
  
 下面的示例生成 C4530:  
  
```  
// C4530.cpp  
// compile with: /W1  
int main() {  
   try{} catch(int*) {}   // C4530  
}  
```  
  
 编译该示例使用 /EHsc 若要解决此警告。