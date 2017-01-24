---
title: "ComPtr::GetAddressOf 方法 | Microsoft Docs"
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
  - "client/Microsoft::WRL::ComPtr::GetAddressOf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetAddressOf 方法"
ms.assetid: 972a41d0-c2ef-4ae3-b2cd-77cc45156ac9
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtr::GetAddressOf 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[ptr\_](../windows/comptr-ptr-data-member.md) 检索数据成员的地址，包含指针到此 ComPtr 表示的接口。  
  
## 语法  
  
```  
T* const* GetAddressOf() const;  
T** GetAddressOf();  
```  
  
## 返回值  
 变量地址。  
  
## 要求  
 **标头：**client.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [ComPtr 类](../windows/comptr-class.md)