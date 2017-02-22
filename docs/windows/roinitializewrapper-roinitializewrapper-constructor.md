---
title: "RoInitializeWrapper::RoInitializeWrapper 构造函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper"
dev_langs: 
  - "C++"
ms.assetid: c6f7fb07-14af-4574-9135-cea164607f30
caps.latest.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 2
---
# RoInitializeWrapper::RoInitializeWrapper 构造函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化 RoInitializeWrapper 类的新实例。  
  
## 语法  
  
```cpp  
RoInitializeWrapper(  
   RO_INIT_TYPE flags)  
  
```  
  
#### 参数  
 `flags`  
 一个枚举，RO\_INIT\_TYPE 指定支持由 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]提供的。  
  
## 备注  
 RoInitializeWrapper 类调用 Windows::Foundation::Initialize\(*flags*\)。  
  
## 要求  
 **标头：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [HandleT 类](../windows/handlet-class.md)