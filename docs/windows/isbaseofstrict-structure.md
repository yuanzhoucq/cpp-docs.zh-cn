---
title: "IsBaseOfStrict 结构 | Microsoft Docs"
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
  - "internal/Microsoft::WRL::Details::IsBaseOfStrict"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsBaseOfStrict 结构"
ms.assetid: 6fed7366-c8d4-4991-b4fb-43ed93f8e1bf
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IsBaseOfStrict 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
template <  
   typename Base,  
   typename Derived  
>  
  
struct IsBaseOfStrict;  
template <  
   typename Base  
>  
struct IsBaseOfStrict<Base, Base>;  
```  
  
#### 参数  
 `Base`  
 基类型。  
  
 `Derived`  
 任何派生类型  
  
## 备注  
 测试某类型是否是另的基础。  
  
 第一个模板测试类型是否从基类型派生，则指定 **true** 或 **false**。  第二个模板测试类型是否从派生，本身始终为 **false**。  
  
## 成员  
  
### 公共常量  
  
|名称|说明|  
|--------|--------|  
|[IsBaseOfStrict::value 常量](../windows/isbaseofstrict-value-constant.md)|指示某类型是否是另的基础。|  
  
## 继承层次结构  
 `IsBaseOfStrict`  
  
## 要求  
 **页眉：**internal.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)