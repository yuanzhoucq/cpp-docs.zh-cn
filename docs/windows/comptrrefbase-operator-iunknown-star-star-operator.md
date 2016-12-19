---
title: "ComPtrRefBase::operator IUnknown** 运算符 | Microsoft Docs"
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
  - "client/Microsoft::WRL::Details::ComPtrRefBase::operator IUnknown**"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator IUnknown** 运算符"
ms.assetid: c2950abf-a7aa-480a-ba41-615703e7f931
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtrRefBase::operator IUnknown** 运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
operator IUnknown**() const;  
```  
  
## 备注  
 模拟当前数据成员设置为指针对 [ptr\_](../windows/comptrrefbase-ptr-data-member.md) 指针对 IUnknown 接口中。  
  
 如果当前 ComPtrRefBase 不是源于 IUnknown，错误发出。  
  
## 要求  
 **标头：**client.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [ComPtrRefBase 类](../windows/comptrrefbase-class.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)