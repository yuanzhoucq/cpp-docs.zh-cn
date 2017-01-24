---
title: "MixIn 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::MixIn"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MixIn 结构"
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MixIn 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

确保的运行时类从 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 接口，如果存在，然后经典 COM 接口派生。  
  
## 语法  
  
```  
template<  
   typename Derived,  
   typename MixInType,  
   bool hasImplements = __is_base_of(Details::ImplementsBase,  
   MixInType)  
>  
struct MixIn;  
```  
  
#### 参数  
 `Derived`  
 从 [实现](../windows/implements-structure.md) 结构派生类型。  
  
 `MixInType`  
 一种基类型。  
  
 `hasImplements`  
 如果`MixInType`派生类型从基类型派生，为 `true`，否则为 `false`。  
  
## 备注  
 如果该类从 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 和 COM 接口派生类，类声明列表必须首先列出所有 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 接口然后任何经典 COM 接口。  接口 MixIn 确保按正确的顺序指定。  
  
## 继承层次结构  
 `MixIn`  
  
## 要求  
 **头文件：**implements.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [Microsoft::WRL 命名空间](../windows/microsoft-wrl-namespace.md)