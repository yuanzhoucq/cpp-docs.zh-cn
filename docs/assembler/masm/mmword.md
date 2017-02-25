---
title: "MMWORD | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MMWORD"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MMWORD directive"
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# MMWORD
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用于具有 MMX 和 SSE \(XMM\) 命令的 64 位多媒体操作数。  
  
## 语法  
  
```  
MMWORD  
```  
  
## 备注  
 `MMWORD` 是类型。 在添加到 MASM 的 MMWORD 之前，等效功能可以借助:  
  
```  
mov mm0, qword ptr [ebx]  
```  
  
 当两个命令处理 64 位操作数时， `QWORD` 为 64 位无符号整数的类型，并 `MMWORD` 是一个 64 位多媒体值的类型。  
  
 `MMWORD` 用于表示类型和 [\_\_m64](../../cpp/m64.md)相同。  
  
## 示例  
  
```  
movq     mm0, mmword ptr [ebx]  
```