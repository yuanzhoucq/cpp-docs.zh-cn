---
title: "ImplementsHelper::FillArrayWithIid 方法 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::Details::ImplementsHelper::FillArrayWithIid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FillArrayWithIid 方法"
ms.assetid: f60035ee-b7d6-4a08-966d-f88c646944c3
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ImplementsHelper::FillArrayWithIid 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
void FillArrayWithIid(  
   _Inout_ unsigned long *index,   
   _Inout_ IID* iids) throw();  
```  
  
#### 参数  
 `index`  
 指示此操作的开始数组元素的从零开始的索引。  当完成此操作时，由 `index` 1. 增加。  
  
 `iids`  
 数组的基础类型IIDs  
  
## 备注  
 用于插入当前 zeroth 模板参数指定的接口 ID 到指定的数组元素。  
  
## 要求  
 **头文件：**implements.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [ImplementsHelper 结构](../windows/implementshelper-structure.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)