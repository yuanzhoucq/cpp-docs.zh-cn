---
title: "ActivationFactoryCallback 函数 | Microsoft Docs"
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
  - "module/Microsoft::WRL::Details::ActivationFactoryCallback"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActivationFactoryCallback 函数"
ms.assetid: dd40c79b-1273-4f2a-8c24-ae9926fb4fd9
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ActivationFactoryCallback 函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
inline HRESULT STDAPICALLTYPE ActivationFactoryCallback(  
   HSTRING activationId,  
   IActivationFactory **ppFactory  
);  
```  
  
#### 参数  
 `activationId`  
 对指定的运行时类名称的字符串处理。  
  
 `ppFactory`  
 该操作完成，对应参数的 `activationId`激活工厂。  
  
## 返回值  
 S\_OK，如果成功；描述，否则失败的 HRESULT。  可能的失败 HRESULT 是 CLASS\_E\_CLASSNOTAVAILABLE 和 E\_INVALIDARG。  
  
## 备注  
 获取指定的 ID. 激活的激活工厂  
  
 Windows 运行时调用该回调函数在请求其运行时类名指定的对象。  
  
## 要求  
 **标头:** module.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)