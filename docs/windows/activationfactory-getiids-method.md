---
title: "ActivationFactory::GetIids 方法 | Microsoft Docs"
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
  - "module/Microsoft::WRL::ActivationFactory::GetIids"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetIids 方法"
ms.assetid: 0983d709-d155-4d65-aae4-5b2c8bb0fede
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ActivationFactory::GetIids 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

检索数组实现的接口 ID。  
  
## 语法  
  
```  
STDMETHOD(  
   GetIids  
)(_Out_ ULONG *iidCount, _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);  
```  
  
#### 参数  
 `iidCount`  
 当完成此操作，interace ID 数在 `iids` 数组中。  
  
 `iids`  
 该操作完成，实现接口 IDs 的数组。  
  
## 返回值  
 S\_OK，如果成功；描述，否则失败的 HRESULT。  E\_OUTOFMEMORY 是可能失败的 HRESULT。  
  
## 要求  
 **标头:** module.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [ActivationFactory 类](../windows/activationfactory-class.md)