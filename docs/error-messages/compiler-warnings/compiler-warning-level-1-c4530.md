---
title: "编译器警告（等级 1）C4530 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4530"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4530"
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4530
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用了 C\+\+ 异常处理程序，但未启用展开语义。请指定 \/EHsc  
  
 使用了 C\+\+ 异常处理，但未选择 [\/EHsc](../../build/reference/eh-exception-handling-model.md)。  
  
 当尚未启用 \/EHsc 选项时，将不销毁框架中具有自动存储的、位于执行引发的函数与捕捉引发的函数之间的对象。  但是将销毁具有自动存储的、在 **try** 块或 **catch** 块中创建的对象。  
  
 下面的示例生成 C4530：  
  
```  
// C4530.cpp  
// compile with: /W1  
int main() {  
   try{} catch(int*) {}   // C4530  
}  
```  
  
 若要解决该警告，请使用 \/EHsc 编译该示例。