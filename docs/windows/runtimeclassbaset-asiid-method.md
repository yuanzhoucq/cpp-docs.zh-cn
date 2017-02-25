---
title: "RuntimeClassBaseT::AsIID 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::RuntimeClassBaseT::AsIID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AsIID 方法"
ms.assetid: 90d7df8a-cf9e-4eef-8837-bc1a25f3fa1a
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# RuntimeClassBaseT::AsIID 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
template<  
   typename T  
>  
__forceinline static HRESULT AsIID(  
   _In_ T* implements,  
   REFIID riid,  
   _Deref_out_ void **ppvObject  
);  
```  
  
#### 参数  
 `T`  
 实现接口 ID 的类型由 `riid`参数指定。  
  
 `implements`  
 模板参数指定类型的变量 `T`。  
  
 `riid`  
 检索要返回的接口 ID。  
  
 `ppvObject`  
 如果该操作成功，指向接口的指针对指针由 `riid`参数指定。  
  
## 返回值  
 S\_OK，如果成功；否则，描述错误的 HRESULT。  
  
## 备注  
 检索特定接口的指针。  
  
## 要求  
 **头文件：**implements.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [RuntimeClassBaseT 结构](../windows/runtimeclassbaset-structure.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)