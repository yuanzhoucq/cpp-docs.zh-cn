---
title: "lock 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "msclr::lock"
  - "msclr.lock"
  - "lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lock 类"
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# lock 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此类采用自动化的访问同步锁为从多个线程中的对象。当构造在获取锁，并且，当销毁它释放锁。  
  
## 语法  
  
```  
ref class lock;  
```  
  
## 备注  
 `lock` 仅用于 CLR 对象，并只能在 CLR 代码。  
  
 在内部，类使用 <xref:System.Threading.Monitor> 阻止同步访问权限。  参见本主题关于同步的更详细信息。  
  
## 要求  
 **Header file** \<msclr\\lock.h\>  
  
 **Namespace** msclr  
  
## 请参阅  
 [锁定](../dotnet/lock.md)   
 [锁定成员](../dotnet/lock-members.md)