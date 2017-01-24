---
title: "ArgTraitsHelper 结构 | Microsoft Docs"
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
  - "event/Microsoft::WRL::Details::ArgTraitsHelper"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ArgTraitsHelper 结构"
ms.assetid: e3f798da-0aef-4a57-95d3-d38c34c47d72
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ArgTraitsHelper 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
template<  
   typename TDelegateInterface  
>  
struct ArgTraitsHelper;  
```  
  
#### 参数  
 `TDelegateInterface`  
 委托接口。  
  
## 备注  
 帮助定义委托参数的公共特性。  
  
## 成员  
  
### 公共 Typedef  
  
|名称|说明|  
|--------|--------|  
|`methodType`|`decltype(&TDelegateInterface::Invoke)`的同义词.|  
|`Traits`|`ArgTraits<methodType>`的同义词.|  
  
### 公共常量  
  
|名称|说明|  
|--------|--------|  
|[ArgTraitsHelper::args 常量](../windows/argtraitshelper-args-constant.md)|帮助 [ArgTraits::args](../windows/argtraits-args-constant.md) 数数目参数数量。委托调用接口的方法。|  
  
## 继承层次结构  
 `ArgTraitsHelper`  
  
## 要求  
 **标头：**event.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)