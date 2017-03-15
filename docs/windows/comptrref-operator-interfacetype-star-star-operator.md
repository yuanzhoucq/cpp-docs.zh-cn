---
title: "ComPtrRef::operator InterfaceType** 运算符 | Microsoft Docs"
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
  - "client/Microsoft::WRL::Details::ComPtrRef::operator InterfaceType**"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator InterfaceType** 运算符"
ms.assetid: b32e3240-a4f0-4998-a55f-d4e35dc9a15a
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtrRef::operator InterfaceType** 运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
operator InterfaceType**();  
```  
  
## 备注  
 删除当前 ComPtrRef 对象并返回指针的指针，指向由 ComPtrRef 对象表示的接口。  
  
## 要求  
 **标头：**client.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [ComPtrRef 类](../windows/comptrref-class.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)