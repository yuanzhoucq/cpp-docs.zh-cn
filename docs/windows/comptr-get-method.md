---
title: "ComPtr::Get 方法 | Microsoft Docs"
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
  - "client/Microsoft::WRL::ComPtr::Get"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Get 方法"
ms.assetid: 078eee51-7bca-4924-a74b-cd4f6a05de31
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtr::Get 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

检索指向与此 ComPtr 关联的接口。  
  
## 语法  
  
```  
T* Get() const;  
```  
  
## 返回值  
 指向与此ComPtr关联的接口的指针。  
  
## 要求  
 **标头：**client.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [ComPtr 类](../windows/comptr-class.md)