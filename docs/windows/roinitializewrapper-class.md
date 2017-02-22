---
title: "RoInitializeWrapper 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper"
dev_langs: 
  - "C++"
ms.assetid: 4055fbe0-63a7-4c06-b5a0-414fda5640e5
caps.latest.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 2
---
# RoInitializeWrapper 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]。  
  
## 语法  
  
```  
class RoInitializeWrapper  
```  
  
## 备注  
 RoInitializeWrapper 是初始化 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 的使用并返回一个 HRESULT 操作是否成功。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[RoInitializeWrapper::RoInitializeWrapper 构造函数](../windows/roinitializewrapper-roinitializewrapper-constructor.md)|初始化 RoInitializeWrapper 类的新实例。|  
|[RoInitializeWrapper::~RoInitializeWrapper 析构函数](../windows/roinitializewrapper-tilde-roinitializewrapper-destructor.md)|销毁 RoInitializeWrapper 类的当前实例。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[RoInitializeWrapper::HRESULT\(\) 运算符](../windows/roinitializewrapper-hresult-parens-operator.md)|检索由最后一个RoInitializeWrapper 构造函数生成的 HRESULT 值。|  
  
## 继承层次结构  
 `RoInitializeWrapper`  
  
## 要求  
 **标头：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [Microsoft::WRL::Wrappers 命名空间](../windows/microsoft-wrl-wrappers-namespace.md)