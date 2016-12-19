---
title: "编译器警告（等级 4）C4234 | Microsoft Docs"
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
  - "C4234"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4234"
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4234
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用了非标准扩展: 保留“keyword”关键字供将来使用  
  
 编译器尚未实现您使用的关键字。  
  
 此警告自动升级为错误。  如果希望修改此行为，请使用 [\#pragma warning](../../preprocessor/warning.md)。  例如，若要使 C4234 成为警告等级 4 问题，  
  
```  
#pragma warning(2:4234)  
```  
  
 请在源代码文件中使用。