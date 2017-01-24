---
title: "编译器警告（等级 2）C4948 | Microsoft Docs"
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
  - "C4948"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4948"
ms.assetid: d006cb17-754a-4c70-ba7f-c3200e2cd8fa
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 2）C4948
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“accessor”的返回类型与相应的 setter 的最后一个参数类型不匹配  
  
 编译器在获取的数据类型和为索引属性设置的数据类型之间找到了不匹配。  
  
 只有使用 **\/clr:oldSyntax** 才可能出现 C4948 警告。  
  
 下面的示例生成 C4948：  
  
```  
// C4948.cpp  
// compile with: /clr:oldSyntax /LD /W2  
  
__gc class MyClass  
{  
   int prop __nogc [2];  
   public:  
  
      __property int get_P(int i)  
      // try the following line instead  
      // __property char get_P(int i)  
      {  
         return prop[i];  
      }  
  
      __property void set_P(int i, char c)  
      {  
         prop[i] = c;  
      }  
};   // C4948  
```