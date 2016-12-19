---
title: "auto_handle 类 | Microsoft Docs"
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
  - "auto_handle, msclr::auto_handle"
  - "msclr.auto_handle"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "auto_handle 类"
ms.assetid: a65604d1-ecbb-44fd-ae2f-696ddeeed9d6
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# auto_handle 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可用于嵌入虚句柄到托管类型的自动管理资源。  
  
## 语法  
  
```  
template<typename _element_type>  
ref class auto_handle;  
```  
  
#### 参数  
 `_element_type`  
 要解析的托管类型将被嵌入。  
  
## 要求  
 **头文件** \<msclr\\auto\_handle.h\>  
  
 **Namespace** msclr  
  
## 请参阅  
 [auto\_handle](../dotnet/auto-handle.md)   
 [auto\_handle 成员](../dotnet/auto-handle-members.md)   
 [auto\_gcroot 类](../dotnet/auto-gcroot-class.md)