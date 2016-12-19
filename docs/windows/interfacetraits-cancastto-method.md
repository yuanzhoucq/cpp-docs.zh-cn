---
title: "InterfaceTraits::CanCastTo 方法 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::Details::InterfaceTraits::CanCastTo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CanCastTo 方法"
ms.assetid: 275847cb-69ea-42bf-910f-05ba6ef8b48d
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# InterfaceTraits::CanCastTo 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
  
template<typename T>  
static __forceinline bool CanCastTo(  
   _In_ T* ptr,  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
  
```  
  
#### 参数  
 `ptr`  
 指针的名称为类型。  
  
 `riid`  
 `Base`接口 ID。  
  
 `ppv`  
 如果该操作成功，给接口的 `ppv` 点由 `Base`指定。  否则，将`ppv`设置为`nullptr` 。  
  
## 返回值  
 `true`，如果该操作成功和 `ptr` 转换到 `Base`的指针；否则，返回 `false`。  
  
## 备注  
 指示指定的指针是否可以转换到 `Base`的指针。  
  
 有关 `Base`的更多信息，请参见 [InterfaceTraits 结构](../windows/interfacetraits-structure.md)Typedefs 的公共部分。  
  
## 要求  
 **头文件：**implements.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [InterfaceTraits 结构](../windows/interfacetraits-structure.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)