---
title: "OPTION (MASM) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "option"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OPTION directive"
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# OPTION (MASM)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

启用和禁用一个汇编的功能。  
  
## 语法  
  
```  
  
OPTION   
optionlist  
  
```  
  
## 备注  
 可用的选项包括:  
  
|||||  
|-|-|-|-|  
|**CASEMAP**|**DOTNAME**|**NODOTNAME**|**模拟器**|  
|**NOEMULATOR**|**收场白**|**EXPR16**|**EXPR32**|  
|**语言**|**LJMP**|**NOLJMP**|**M510**|  
|**NOM510**|**NOKEYWORD**|**NOSIGNEXTEND**|**偏移量**|  
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|  
|**PROC**|**prolog**|**READONLY**|**NOREADONLY**|  
|**SCOPED**|**NOSCOPED**|**段**|**SETIF2**。|  
  
 语言的语法是 **选项语言:***x*，其中 *x* 是一个 C、 SYSCALL、 STDCALL、 PASCAL、 FORTRAN 或 BASIC。  SYSCALL、 PASCAL、编写和 BASIC 不支持使用与 [.MODEL](../../assembler/masm/dot-model.md) 简单列表。  
  
## 请参阅  
 [Directives Reference](../../assembler/masm/directives-reference.md)