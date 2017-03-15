---
title: "复合语句（块） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "}"
  - "{"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "块, 关于块"
  - "复合语句"
ms.assetid: 23855939-7430-498e-8936-0c70055ea701
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 复合语句（块）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

复合语句包含封闭在大括号 \(**{ }**\) 中的零个或多个语句。  可以在任何期望语句出现的位置使用复合语句。  复合语句通常称为“块”。  
  
## 语法  
  
```  
  
{ [ statement-list ] }  
```  
  
## 备注  
 以下示例使用复合语句作为 **if** 语句的 *statement* 部分（有关语法的详细信息，请参阅 [if 语句](../cpp/if-else-statement-cpp.md)）：  
  
```  
if( Amount > 100 )  
{  
    cout << "Amount was too large to handle\n";  
    Alert();  
}  
else  
    Balance -= Amount;  
```  
  
> [!NOTE]
>  由于声明是一个语句，因此声明可以是 *statement\-list* 内的某个语句。  因此，复合语句内声明的名称（而不是显式声明为静态的名称）具有局部范围和（对于对象）生存期。  有关处理带局部范围的名称的详细信息，请参阅[范围](../cpp/scope-visual-cpp.md)。  
  
## 请参阅  
 [C\+\+ 语句概述](../cpp/overview-of-cpp-statements.md)