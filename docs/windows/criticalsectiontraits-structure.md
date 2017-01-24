---
title: "CriticalSectionTraits 结构 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CriticalSectionTraits 结构"
ms.assetid: c515a1b5-4eb0-40bc-9035-c4d9352c9de7
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CriticalSectionTraits 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

专用CriticalSection对象支持无效关键部分或功能的关键部分。  
  
## 语法  
  
```  
struct CriticalSectionTraits;  
```  
  
## 成员  
  
### 公共 Typedef  
  
|名称|说明|  
|--------|--------|  
|`Type`|定义了指向关键部分的 `typedef`。  `Type` 被定义为 `typedef CRITICAL_SECTION* Type;`：|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CriticalSectionTraits::GetInvalidValue 方法](../windows/criticalsectiontraits-getinvalidvalue-method.md)|专用 CriticalSection 模板，以便模板中始终无效。|  
|[CriticalSectionTraits::Unlock 方法](../windows/criticalsectiontraits-unlock-method.md)|专用 CriticalSection 模板，以便支持释放指定的临界区对象的所有权。|  
  
## 继承层次结构  
 `CriticalSectionTraits`  
  
## 要求  
 **标头：**corewrappers.h  
  
 Microsoft::WRL::Wrappers::HandleTraits **命名空间:**  
  
## 请参阅  
 [Microsoft::WRL::Wrappers::HandleTraits 命名空间](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)