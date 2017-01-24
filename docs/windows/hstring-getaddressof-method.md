---
title: "HString::GetAddressOf 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HString::GetAddressOf"
dev_langs: 
  - "C++"
ms.assetid: 6050decf-5f99-49f0-9497-1c8192c485ae
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HString::GetAddressOf 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

检索基础 HSTRING 句柄的指针。  
  
## 语法  
  
```  
HSTRING* GetAddressOf() throw()  
```  
  
## 返回值  
 基础 HSTRING 句柄的指针。  
  
## 备注  
 此操作后，HSTRING 销毁基础句柄的字符串值。  
  
## 要求  
 **标头：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [HString 类](../windows/hstring-class.md)