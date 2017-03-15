---
title: "BoolStruct 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "internal/Microsoft::WRL::Details::BoolStruct"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BoolStruct 结构"
ms.assetid: 666eae78-e81d-4fb7-a9e4-1ba617d6d4cd
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# BoolStruct 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
struct BoolStruct;  
```  
  
## 备注  
 BoolStruct 结构定义 ComPtr 是否管理接口的对象生存期。  [BoolType\(\)](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md) 运算符在内部使用 BoolStruct。  
  
## 成员  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[BoolStruct::Member 数据成员](../windows/boolstruct-member-data-member.md)|指定是 [ComPtr](../windows/comptr-class.md)，或若非，管理接口的对象生存期。|  
  
## 继承层次结构  
 `BoolStruct`  
  
## 要求  
 **页眉：**internal.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)   
 [ComPtr::operator Microsoft::WRL::Details::BoolType 运算符](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)