---
title: "RuntimeClassBaseT::GetImplementedIIDS 方法 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetImplementedIIDS 方法"
ms.assetid: adae54da-521d-4add-87f5-242fbd85f33b
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RuntimeClassBaseT::GetImplementedIIDS 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
template<  
   typename T  
>  
__forceinline static HRESULT GetImplementedIIDS(  
   _In_ T* implements,  
   _Out_ ULONG *iidCount,  
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids  
);  
```  
  
#### 参数  
 `T`  
 `implements` 参数的类型。  
  
 `implements`  
 为参数指定类型的 `T`指针。  
  
 `iidCount`  
 接口 ID 的最大数字检索的。  
  
 `iids`  
 如果该操作成功完成，接口 ID 的数组由 `T`类型实现的。  
  
## 返回值  
 S\_OK，如果成功；否则，描述错误的 HRESULT。  
  
## 备注  
 检索数组由指定的类型实现的接口 ID。  
  
## 要求  
 **头文件：**implements.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [RuntimeClassBaseT 结构](../windows/runtimeclassbaset-structure.md)