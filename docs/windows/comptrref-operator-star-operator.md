---
title: "ComPtrRef::operator* 运算符 | Microsoft Docs"
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
  - "client/Microsoft::WRL::Details::ComPtrRef::operator*"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator* 运算符"
ms.assetid: 0287ca7a-4ce1-47f7-bab6-714fca3e04bb
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtrRef::operator* 运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
InterfaceType* operator *();  
```  
  
## 返回值  
 指向 ComPtrRef 对象表示接口的指针。  
  
## 备注  
 检索指向 ComPtrRef 对象表示接口的指针。  
  
## 要求  
 **标头：**client.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [ComPtrRef 类](../windows/comptrref-class.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)