---
title: "HANDLENullTraits 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "HANDLENullTraits 结构"
ms.assetid: 88a29a14-c516-40cb-a0ca-ee897a668623
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# HANDLENullTraits 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义未初始化句柄的常见特性。  
  
## 语法  
  
```  
struct HANDLENullTraits;  
```  
  
## 成员  
  
### 公共 Typedef  
  
|名称|说明|  
|--------|--------|  
|`Type`|是图柄的同义词。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[HANDLENullTraits::Close 方法](../windows/handlenulltraits-close-method.md)|关闭指定的句柄。|  
|[HANDLENullTraits::GetInvalidValue 方法](../windows/handlenulltraits-getinvalidvalue-method.md)|表示无效的句柄。|  
  
## 继承层次结构  
 `HANDLENullTraits`  
  
## 要求  
 **标头：**corewrappers.h  
  
 Microsoft::WRL::Wrappers::HandleTraits **命名空间:**  
  
## 请参阅  
 [Microsoft::WRL::Wrappers::HandleTraits 命名空间](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)