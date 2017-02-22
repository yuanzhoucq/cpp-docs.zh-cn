---
title: "CreatorMap::activationId 数据成员 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Details::CreatorMap::activationId"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "activationId 数据成员"
ms.assetid: 77518b76-6e6a-4b48-8e2e-a4c7c67769e0
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# CreatorMap::activationId 数据成员
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
union {   
   const IID* clsid;  
   const wchar_t* (*getRuntimeName)();  
} activationId;  
```  
  
## 参数  
 `clsid`  
 是一个ID接口。  
  
 `getRuntimeName`  
 检索对象的 Windows 上运行时名称的函数。  
  
## 备注  
 表示由经典 COM 类 ID 或窗口运行时名称标识的对象 ID。  
  
## 要求  
 **标头:** module.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [CreatorMap 结构](../windows/creatormap-structure.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)