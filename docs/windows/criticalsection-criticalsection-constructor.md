---
title: "CriticalSection::CriticalSection 构造函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::CriticalSection::CriticalSection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CriticalSection, 构造函数"
ms.assetid: 930b89be-4d74-46bd-8879-5dd4d15bcbd0
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# CriticalSection::CriticalSection 构造函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化类似 Mutex 对象的同步对象，但是，可以由单个进程中只使用线程。  
  
## 语法  
  
```  
explicit CriticalSection(  
   ULONG spincount = 0  
);  
```  
  
#### 参数  
 `spincount`  
 设置临界区对象的重试次数。  默认值为 0。  
  
## 备注  
 有关 crticial 节和 spincounts 的更多信息，请参见" Windows API documenation 的同步节的 **InitializeCriticalSectionAndSpinCount** 函数。  
  
## 要求  
 **标头：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [CriticalSection 类](../windows/criticalsection-class.md)