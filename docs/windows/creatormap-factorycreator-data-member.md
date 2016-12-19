---
title: "CreatorMap::factoryCreator 数据成员 | Microsoft Docs"
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
  - "module/Microsoft::WRL::Details::CreatorMap::factoryCreator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "factoryCreator 数据成员"
ms.assetid: c9aac363-8f38-4cfd-9605-1e6ac74c5097
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CreatorMap::factoryCreator 数据成员
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
HRESULT (*factoryCreator)(  
   unsigned int* currentflags,  
   const CreatorMap* entry,  
   REFIID iidClassFactory,  
 IUnknown** factory);  
```  
  
## 参数  
 `currentflags`  
 一个枚举器。[RuntimeClassType](../windows/runtimeclasstype-enumeration.md)  
  
 `entry`  
 CreatorMap。  
  
 `iidClassFactory`  
 类工厂的接口 ID。  
  
 `factory`  
 完成操作，类工厂的地址。  
  
## 返回值  
 S\_OK，如果成功；否则，一错误的 HRESULT。  
  
## 备注  
 创建指定的 CreatorMap 的工厂。  
  
## 要求  
 **标头:** module.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [CreatorMap 结构](../windows/creatormap-structure.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)