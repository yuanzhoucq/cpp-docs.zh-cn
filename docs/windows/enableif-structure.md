---
title: "EnableIf 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "internal/Microsoft::WRL::Details::EnableIf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "EnableIf 结构"
ms.assetid: 7825b283-e6b2-4f39-a4b9-c03bcd431b8e
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# EnableIf 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
template <  
   bool b,  
   typename T = void  
>  
  
struct EnableIf;  
template <  
   typename T  
>  
struct EnableIf<true, T>;  
```  
  
#### 参数  
 `T`  
 一个类型。  
  
 `b`  
 布尔表达式。  
  
## 备注  
 模板，如果第一个参数的计算结果为 `true`，将第二个定义模板参数指定类型的数据成员。  
  
## 成员  
  
### 公共 Typedef  
  
|名称|说明|  
|--------|--------|  
|`type`|如果模板参数 `b` 的计算结果为 `true`，则部分专用化定义数据成员 `type` 是 `T`类型。|  
  
## 继承层次结构  
 `EnableIf`  
  
## 要求  
 **页眉：**internal.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)