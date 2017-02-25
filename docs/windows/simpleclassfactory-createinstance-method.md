---
title: "SimpleClassFactory::CreateInstance 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::SimpleClassFactory::CreateInstance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateInstance 方法"
ms.assetid: 17b7947a-2608-49d9-b730-fef76501c9bc
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# SimpleClassFactory::CreateInstance 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

创建指定接口的实例。  
  
## 语法  
  
```  
  
STDMETHOD(  
   CreateInstance  
)  
   (_Inout_opt_ IUnknown* pUnkOuter,   
   REFIID riid,   
   _Deref_out_ void** ppvObject);  
```  
  
#### 参数  
 `pUnkOuter`  
 必须为 `nullptr`;否则，返回值是 CLASS\_E\_NOAGGREGATION。  
  
 SimpleClassFactory 不支持聚合。  如果聚合支持，并且要创建的对象都是聚合的一部分，`pUnkOuter` 是指向对聚合的控制由接口的指针。  
  
 `riid`  
 创建的对象的接口 ID。  
  
 `ppvObject`  
 该操作完成，对 `riid` 参数指定的对象实例的指针。  
  
## 返回值  
 S\_OK，如果成功；否则，一错误的 HRESULT。  
  
## 备注  
 如果\_\_WRL\_STRICT 定义，断言错误发出，如果 [](../windows/runtimeclass-class.md "RuntimeClass Class")[类模板参数指定类从](../windows/runtimeclasstype-enumeration.md)基类未派生，也不使用配置 ClassicCom 或 RuntimeClassType WinRtClassicComMix 枚举值。  
  
## 要求  
 **标头:** module.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [SimpleClassFactory 类](../windows/simpleclassfactory-class.md)