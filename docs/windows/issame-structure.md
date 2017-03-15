---
title: "IsSame 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "internal/Microsoft::WRL::Details::IsSame"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsSame 结构"
ms.assetid: 1eddbc3f-3cc5-434f-8495-e4477e1f868e
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# IsSame 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
template <  
   typename T1,  
   typename T2  
>  
struct IsSame;  
template <  
   typename T1  
>  
struct IsSame<T1, T1>;  
```  
  
#### 参数  
 `T1`  
 一个类型。  
  
 `T2`  
 另一个类型。  
  
## 备注  
 测试指定的类型是否与另一指定的类型相同。  
  
## 成员  
  
### 公共常量  
  
|名称|说明|  
|--------|--------|  
|[IsSame::value 常量](../windows/issame-value-constant.md)|指示某类型是否与另一个。|  
  
## 继承层次结构  
 `IsSame`  
  
## 要求  
 **页眉：**internal.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)