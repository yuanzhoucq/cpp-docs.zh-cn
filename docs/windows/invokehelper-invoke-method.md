---
title: "InvokeHelper::Invoke 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "event/Microsoft::WRL::Details::InvokeHelper::Invoke"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Invoke 方法"
ms.assetid: 98618815-c30e-4699-b3dd-203c91b1bf3b
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# InvokeHelper::Invoke 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
STDMETHOD(  
   Invoke  
)();  
STDMETHOD(  
   Invoke  
)(typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
```  
  
#### 参数  
 `arg1`  
 参数1。  
  
 `arg2`  
 参数2。  
  
 `arg3`  
 参数3。  
  
 `arg4`  
 参数4。  
  
 `arg5`  
 参数5。  
  
 `arg6`  
 参数6。  
  
 `arg7`  
 参数7。  
  
 `arg8`  
 参数8。  
  
 `arg9`  
 参数9。  
  
## 返回值  
 S\_OK，如果成功；否则，描述错误的 HRESULT。  
  
## 备注  
 调用签名包含参数的指定的事件处理程序。  
  
## 要求  
 **标头：**event.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [InvokeHelper 结构](../windows/invokehelper-structure.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)