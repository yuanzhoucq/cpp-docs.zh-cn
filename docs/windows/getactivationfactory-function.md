---
title: "GetActivationFactory 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Details::GetActivationFactory"
  - "client/ABI::Windows::Foundation::GetActivationFactory"
  - "client/Windows::Foundation::GetActivationFactory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetActivationFactory 函数"
ms.assetid: 5736d285-6beb-42aa-8788-e261c0010afe
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# GetActivationFactory 函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要检索模板参数指定类型的激活一个工厂。  
  
## 语法  
  
```  
template<  
   typename T  
>  
inline HRESULT GetActivationFactory(  
   _In_ HSTRING activatableClassId,  
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> factory  
);  
```  
  
#### 参数  
 `T`  
 指定激活工厂的类型模板参数。  
  
 `activatableClassId`  
 激活可导致类工厂的名称。  
  
 `factory`  
 该操作完成，对工厂的活动引用类型的 `T`。  
  
## 返回值  
 S\_OK，如果成功；否则，一个错误 HRESULT 此操作失败的原因。  
  
## 要求  
 **标头：**client.h  
  
 Windows::Foundation**Namespace:**  
  
## 请参阅  
 [Windows::Foundation 命名空间](../windows/windows-foundation-namespace.md)