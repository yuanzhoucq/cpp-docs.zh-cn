---
title: "ChainInterfaces::CanCastTo 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::ChainInterfaces::CanCastTo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CanCastTo 方法"
ms.assetid: 8be44875-53ed-494b-91a0-0f8e399685bb
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# ChainInterfaces::CanCastTo 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示指定接口 ID 是否可以转换为非默认的模板参数定义的每一专用化。  
  
## 语法  
  
```  
__forceinline bool CanCastTo(  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
```  
  
#### 参数  
 `riid`  
 是一个ID接口。  
  
 `ppv`  
 成功转换到最后一个接口 ID 的指针。  
  
## 返回值  
 `true`，如果任何转换操作成功；否则，返回 `false`。  
  
## 要求  
 **头文件：**implements.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [ChainInterfaces 结构](../windows/chaininterfaces-structure.md)