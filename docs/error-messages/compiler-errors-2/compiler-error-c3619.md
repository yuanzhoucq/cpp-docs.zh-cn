---
title: "编译器错误 C3619 | Microsoft Docs"
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
  - "C3619"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3619"
ms.assetid: 76ae80d0-9fbe-4297-a1ef-b1503377fdcf
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3619
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不能在托管或 WinRT 类型中声明模板  
  
 不允许在托管或 WinRT 类或接口使用类模板。  
  
 C3619 只能使用 **\/clr:oldSyntax** 获得。  
  
 以下示例生成 C3619：  
  
```  
// C3619.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__gc class X {  
   template<typename T> class Y {   // C3619  
   };  
};  
```