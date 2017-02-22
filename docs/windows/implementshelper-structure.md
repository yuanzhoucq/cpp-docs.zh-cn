---
title: "ImplementsHelper 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::ImplementsHelper"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ImplementsHelper 结构"
ms.assetid: b857ba80-81bd-4e53-92b6-210991954243
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# ImplementsHelper 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
template <  
   typename RuntimeClassFlagsT,  
   typename ILst,  
   bool IsDelegateToClass  
>  
friend struct Details::ImplementsHelper;  
```  
  
#### 参数  
 `RuntimeClassFlagsT`  
 指定一个或多个 [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) 枚举数的字段。  
  
 `ILst`  
 接口IDs的列表。  
  
 `IsDelegateToClass`  
 如果实现，当前实例作为第一个接口 ID 的基类。`ILst`，则指定 `true` ;否则，返回 `false`。  
  
## 备注  
 帮助实现 [实现](../windows/implements-structure.md) 结构。  
  
 遍历此模板接口列表并将它们用作基类并且作为必需的信息允许 QueryInterface。  
  
## 成员  
  
## 继承层次结构  
 `ImplementsHelper`  
  
## 要求  
 **头文件：**implements.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [Reference \(Windows Runtime Library\)](http://msdn.microsoft.com/zh-cn/00000000-0000-0000-0000-000000000000)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)