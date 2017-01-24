---
title: "Microsoft::WRL::Wrappers::Details 命名空间 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::Details"
  - "internal/Microsoft::WRL::Details"
  - "async/Microsoft::WRL::Details"
  - "corewrappers/Microsoft::WRL::Wrappers::Details"
  - "client/Microsoft::WRL::Details"
  - "module/Microsoft::WRL::Details"
  - "event/Microsoft::WRL::Details"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Details 命名空间"
ms.assetid: 6d3f04ac-9b53-4a82-a188-a85309ec34a4
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Microsoft::WRL::Wrappers::Details 命名空间
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
namespace Microsoft::WRL::Wrappers::Details;  
```  
  
## 成员  
  
### 类  
  
|名称|说明|  
|--------|--------|  
|[SyncLockT 类](../windows/synclockt-class.md)|呈现可以排除或采用资源的共享所有权的类型。|  
|[SyncLockWithStatusT 类](../windows/synclockwithstatust-class.md)|呈现可以排除或采用资源的共享所有权的类型。|  
  
### 方法  
  
|名称|说明|  
|--------|--------|  
|[CompareStringOrdinal 方法](../windows/comparestringordinal-method.md)|比较两个指定的 `HSTRING` 对象，并返回一个指示二者在排序顺序中的相对位置的整数。|  
  
## 要求  
 **标头：**corewrappers.h  
  
 Microsoft::WRL::Wrappers::Details**命名空间:**  
  
## 请参阅  
 [Microsoft::WRL::Wrappers 命名空间](../windows/microsoft-wrl-wrappers-namespace.md)