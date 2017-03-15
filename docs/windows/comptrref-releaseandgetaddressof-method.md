---
title: "ComPtrRef::ReleaseAndGetAddressOf 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Microsoft::WRL::Details::ComPtrRef::ReleaseAndGetAddressOf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ReleaseAndGetAddressOf 方法"
ms.assetid: 004aac42-e135-41ce-8d1d-4c5969d55004
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# ComPtrRef::ReleaseAndGetAddressOf 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
InterfaceType** ReleaseAndGetAddressOf();  
```  
  
## 返回值  
 指向接口由删除的ComPtrRef对象呈现的接口的指针。  
  
## 备注  
 删除当前 ComPtrRef 对象并返回指针的指针，指向由 ComPtrRef 对象表示的接口。  
  
## 要求  
 **标头：**client.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [ComPtrRef 类](../windows/comptrref-class.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)