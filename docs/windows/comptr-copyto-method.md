---
title: "ComPtr::CopyTo 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Microsoft::WRL::ComPtr::CopyTo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CopyTo 方法"
ms.assetid: 8801bc49-6db4-4393-a55f-a701ae3b8718
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# ComPtr::CopyTo 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

复制当前或指定接口与此 ComPtr 对指定的指针。  
  
## 语法  
  
```  
HRESULT CopyTo(  
   _Deref_out_ InterfaceType** ptr  
);  
  
HRESULT CopyTo(  
   REFIID riid,  
   _Deref_out_ void** ptr  
) const;  
template<  
   typename U  
>  
  
HRESULT CopyTo(  
   _Deref_out_ U** ptr  
) const;  
```  
  
#### 参数  
 `U`  
 类型名称。  
  
 `ptr`  
 该操作完成，对请求接口的指针。  
  
 `riid`  
 是一个ID接口。  
  
## 返回值  
 S\_OK，如果成功；否则，一个 HRESULT 隐式 QueryInterface 操作失败的原因。  
  
## 备注  
 第一个函数返回指针的复制到与此接口 ComPtr。  此函数始终返回 S\_OK。  
  
 第二个函数对接口的 QueryInterface 操作与 `riid` 参数指定的接口 ComPtr 此。  
  
 第三个函数对接口的 QueryInterface 操作与 `U` 参数的基础接口的此 ComPtr。  
  
## 要求  
 **标头：**client.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [ComPtr 类](../windows/comptr-class.md)