---
title: "编译器警告（等级 4）C4235 | Microsoft Docs"
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
  - "C4235"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4235"
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4235
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用了非标准扩展: 不支持在此结构上使用“keyword”关键字  
  
 编译器不支持您使用的关键字。  
  
 此警告自动升级为错误。  如果希望修改此行为，请使用 [\#pragma warning](../../preprocessor/warning.md)。  例如，若要使 C4235 成为等级 2 警告，  
  
```  
#pragma warning(2:4235)  
```  
  
 请在源代码文件中使用。