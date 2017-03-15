---
title: "CloakedIid 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::CloakedIid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CloakedIid 结构"
ms.assetid: 82e0e377-ca3a-46bc-b850-ae2c46c15bb5
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# CloakedIid 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

来 RuntimeClass、实现和 ChainInterfaces 模板指定接口是不可访问的。IID 列表。  
  
## 语法  
  
```  
template<  
   typename T  
>  
struct CloakedIid : T;  
```  
  
#### 参数  
 `T`  
 隐藏的接口 \(掩蔽\)。  
  
## 备注  
 下面是有关如何使用 CloakedIid: `struct MyRuntimeClass : RuntimeClass<CloakedIid<IMyCloakedInterface>> {}`。  
  
## 继承层次结构  
 `T`  
  
 `CloakedIid`  
  
## 要求  
 **头文件：**implements.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [Microsoft::WRL 命名空间](../windows/microsoft-wrl-namespace.md)