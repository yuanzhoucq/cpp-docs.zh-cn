---
title: "__wbinvd | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__wbinvd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__wbinvd 内部函数"
  - "wbinvd 指令"
ms.assetid: 628d0981-39e5-49e1-bd43-706d123af121
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# __wbinvd
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 生成回复和无效缓存 \(`wbinvd`\) 命令。  
  
## 语法  
  
```  
void __wbinvd(void);  
```  
  
## 要求  
  
|内部|体系结构|  
|--------|----------|  
|`__wbinvd`|x86， [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **头文件** \<intrin.h\>  
  
## 备注  
 此功能只有在具有权限级别 \(CPL\) 的核心架构的 0，并且，实例只能用作内部。  
  
## 特定于 Microsoft 的结尾  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)