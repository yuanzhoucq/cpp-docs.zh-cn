---
title: "ActivateInstance 函数 | Microsoft Docs"
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
  - "client/Windows::Foundation::ActivateInstance"
  - "client/ABI::Windows::Foundation::ActivateInstance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActivateInstance 函数"
ms.assetid: 8cfd1dd9-5fda-4cc2-acf8-d40e783b3875
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ActivateInstance 函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

注册和检索中所指定的类 ID. 定义中指定的类型的实例  
  
## 语法  
  
```  
template<  
   typename T  
>  
inline HRESULT ActivateInstance(  
   _In_ HSTRING activatableClassId,  
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> instance  
);  
```  
  
#### 参数  
 `T`  
 要激活的类型。  
  
 `activatableClassId`  
 定义参数 `T`类 ID 的名称。  
  
 `instance`  
 该操作完成，对 `T`实例的引用。  
  
## 返回值  
 S\_OK，如果成功；否则，一错误的原因的错误 HRESULT。  
  
## 要求  
 **标头：**client.h  
  
 Windows::Foundation**Namespace:**  
  
## 请参阅  
 [Windows::Foundation 命名空间](../windows/windows-foundation-namespace.md)