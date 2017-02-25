---
title: "SimpleActivationFactory::ActivateInstance 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::SimpleActivationFactory::ActivateInstance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActivateInstance 方法"
ms.assetid: 4f836e51-5a6c-4bad-b871-9f25199298b4
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# SimpleActivationFactory::ActivateInstance 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

创建指定接口的实例。  
  
## 语法  
  
```  
STDMETHOD(  
   ActivateInstance  
)(_Deref_out_ IInspectable **ppvObject);  
```  
  
#### 参数  
 `ppvObject`  
 该操作完成，对 `Base` 类模板参数指定的对象实例的指针。  
  
## 返回值  
 S\_OK，如果成功；否则，一错误的 HRESULT。  
  
## 备注  
 如果\_\_WRL\_STRICT 定义，断言错误发出，如果 [](../windows/runtimeclass-class.md "RuntimeClass Class")[类模板参数指定类从](../windows/runtimeclasstype-enumeration.md)基类未派生，也不使用配置 WinRt 或 RuntimeClassType WinRtClassicComMix 枚举值。  
  
## 要求  
 **标头:** module.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [SimpleActivationFactory 类](../windows/simpleactivationfactory-class.md)