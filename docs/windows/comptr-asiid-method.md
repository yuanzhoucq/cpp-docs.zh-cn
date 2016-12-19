---
title: "ComPtr::AsIID 方法 | Microsoft Docs"
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
  - "client/Microsoft::WRL::ComPtr::AsIID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AsIID 方法"
ms.assetid: d5a3cdb2-796d-4410-966a-847c0e8fb226
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtr::AsIID 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

返回表示指定的接口ID的接口的 ComPtr 对象。  
  
## 语法  
  
```  
WRL_NOTHROW HRESULT AsIID(  
   REFIID riid,  
   _Out_ ComPtr<IUnknown>* p  
) const;  
```  
  
#### 参数  
 `riid`  
 是一个ID接口。  
  
 `p`  
 如果支持，双间接指针为 `riid` 参数指定的接口；否则，为由的指针。  
  
## 返回值  
 S\_OK，如果成功；否则，一错误的 HRESULT。  
  
## 要求  
 **标头：**client.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [ComPtr 类](../windows/comptr-class.md)