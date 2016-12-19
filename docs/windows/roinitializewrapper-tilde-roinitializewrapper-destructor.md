---
title: "RoInitializeWrapper::~RoInitializeWrapper 析构函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::~RoInitializeWrapper"
dev_langs: 
  - "C++"
ms.assetid: afef4c1f-ffde-4cd2-8654-8de4182eb5f4
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RoInitializeWrapper::~RoInitializeWrapper 析构函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

未初始化 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]。  
  
## 语法  
  
```cpp  
~RoInitializeWrapper()  
```  
  
## 备注  
 RoInitializeWrapper 类调用 Windows::Foundation::Uninitialize\(\)。  
  
## 要求  
 **标头：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [HandleT 类](../windows/handlet-class.md)