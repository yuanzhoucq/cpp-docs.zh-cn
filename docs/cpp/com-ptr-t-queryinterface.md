---
title: "_com_ptr_t::QueryInterface | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_ptr_t::QueryInterface"
  - "_com_ptr_t.QueryInterface"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "QueryInterface 方法"
ms.assetid: d03292f1-6b02-40db-9756-8b0837a97319
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# _com_ptr_t::QueryInterface
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 调用封装的接口指针上的 **IUnknown** 的 `QueryInterface` 成员函数。  
  
## 语法  
  
```  
  
      template<typename _InterfaceType> HRESULT QueryInterface (  
   const IID& iid,  
   _InterfaceType*& p   
) throw ( );  
template<typename _InterfaceType> HRESULT QueryInterface (  
   const IID& iid,  
   _InterfaceType** p  
) throw( );  
```  
  
#### 参数  
 `iid`  
 接口指针的 **IID**。  
  
 `p`  
 原始接口指针。  
  
## 备注  
 对具有指定 **IID** 的已封装接口指针调用 **IUnknown::QueryInterface** 并返回 `p` 中生成的原始接口指针。  此例程返回 `HRESULT` 以指示成功或失败。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_com\_ptr\_t 类](../cpp/com-ptr-t-class.md)