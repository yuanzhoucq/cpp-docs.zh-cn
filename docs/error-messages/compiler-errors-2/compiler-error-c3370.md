---
title: "编译器错误 C3370 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3370"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3370"
ms.assetid: ee6d4c85-78fc-42b2-836e-5cc491a3b2ba
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3370
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“idl\_module nam”：idl\_module 尚未定义  
  
 使用 [idl\_module](../../windows/idl-module.md) 在 DLL 中指定入口点前，必须首先使用 `idl_module` 指定 DLL 名称。  
  
 以下示例生成 C3370：  
  
```  
// C3370.cpp [module(name=MyLibrary)]; // uncomment the following line to resolve the error // [idl_module(name="name1", dllname=x.dll)]; [idl_module(name="name1"), entry(100)] // C3370 int f1(); int main() { }  
```