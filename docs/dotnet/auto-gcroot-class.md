---
title: "auto_gcroot 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "msclr::auto_gcroot"
  - "msclr.auto_gcroot"
  - "auto_gcroot"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "auto_gcroot"
ms.assetid: b5790912-265d-463e-a486-47302e91042a
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# auto_gcroot 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可用于嵌入虚句柄到本机类型的自动资源管理 \(如 [auto\_ptr 类](../standard-library/auto-ptr-class.md)\)。  
  
## 语法  
  
```  
template<typename _element_type>  
class auto_gcroot;  
```  
  
#### 参数  
 `_element_type`  
 将嵌入的托管类型。  
  
## 要求  
 **头文件** \<msclr \\ auto\_gcroot.h\>  
  
 **命名空间** msclr  
  
## 请参阅  
 [auto\_gcroot](../dotnet/auto-gcroot.md)   
 [auto\_gcroot Members](../dotnet/auto-gcroot-members.md)   
 [如何：使用本机类型声明句柄](../dotnet/how-to-declare-handles-in-native-types.md)   
 [auto\_handle 类](../dotnet/auto-handle-class.md)