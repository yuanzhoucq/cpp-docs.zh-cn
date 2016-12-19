---
title: "jitintrinsic | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "jitintrinsic"
  - "jitintrinsic_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 关键字 [C++], jitintrinsic"
  - "jitintrinsic __declspec 修饰符"
ms.assetid: 23dbe416-7ef6-442b-b16d-9a81aab04fa6
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# jitintrinsic
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将函数标记为对 64 位公共语言运行时很有用。  这用于 Microsoft 提供的库中的某些函数。  
  
## 语法  
  
```  
__declspec(jitintrinsic)  
```  
  
## 备注  
 `jitintrinsic` 将 MODOPT \(<xref:System.Runtime.CompilerServices.IsJitIntrinsic>\) 添加到函数签名。  
  
 禁止用户使用该 `__declspec` 修饰符，因为可能出现意外结果。  
  
## 请参阅  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)