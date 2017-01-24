---
title: "编译器错误 C3812 | Microsoft Docs"
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
  - "C3812"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3812"
ms.assetid: 326ac706-9a5f-4851-b9d2-b90c64c75532
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3812
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“property”必须是属性声明的第一个标记  
  
 声明属性时，[\_\_property](../../misc/property.md) 关键字必须是该行内的第一个标记。  
  
 只有使用 **\/clr:oldSyntax** 才可以访问 C3812。  
  
 下面的示例生成 C3812：  
  
```  
// C3812.cpp  
// compile with: /clr:oldSyntax /c  
#using <mscorlib.dll>  
  
__gc class X {  
   static __property int get_Size() { // C3812, remove static specifier  
      return 0;  
   }  
};  
```