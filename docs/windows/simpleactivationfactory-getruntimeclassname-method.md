---
title: "SimpleActivationFactory::GetRuntimeClassName 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName"
dev_langs: 
  - "C++"
ms.assetid: 3aa07487-9a42-46f8-8893-37ba6315e50b
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# SimpleActivationFactory::GetRuntimeClassName 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

获取类实例的运行时类名 `Base` 类模板参数指定的。  
  
## 语法  
  
```  
STDMETHOD(  
   GetRuntimeClassName  
)(_Out_ HSTRING* runtimeName);  
```  
  
#### 参数  
 `runtimeName`  
 该操作完成，运行时类名。  
  
## 返回值  
 S\_OK，如果成功；否则，一错误的 HRESULT。  
  
## 备注  
 如果\_\_WRL\_STRICT 定义，断言错误发出，如果 `Base` 类模板参数指定类从 [RuntimeClass](../windows/runtimeclass-class.md)未派生，也不使用配置 WinRt 或 [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) WinRtClassicComMix 枚举值。  
  
## 要求  
 **标头:** module.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [SimpleActivationFactory 类](../windows/simpleactivationfactory-class.md)