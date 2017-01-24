---
title: "ComPtr::ReleaseAndGetAddressOf 方法 | Microsoft Docs"
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
  - "client/Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ReleaseAndGetAddressOf 方法"
ms.assetid: 3751dcb4-d50e-432c-89e4-e736be34d434
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtr::ReleaseAndGetAddressOf 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

释放接口与此 ComPtr 然后检索 [ptr\_](../windows/comptr-ptr-data-member.md) 数据成员的地址，包含一个指向接口被释放。  
  
## 语法  
  
```  
T** ReleaseAndGetAddressOf();  
```  
  
## 返回值  
 此 ComPtr 的 [ptr\_](../windows/comptr-ptr-data-member.md) 数据成员的地址。  
  
## 要求  
 **标头：**client.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [ComPtr 类](../windows/comptr-class.md)   
 [ComPtr::ptr\_ 数据成员](../windows/comptr-ptr-data-member.md)