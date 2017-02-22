---
title: "RuntimeClassBaseT 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::RuntimeClassBaseT"
dev_langs: 
  - "C++"
ms.assetid: a62775fb-3359-4f45-9ff1-c07fa8da464b
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# RuntimeClassBaseT 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
template <  
   unsigned int RuntimeClassTypeT  
>  
friend struct Details::RuntimeClassBaseT;  
```  
  
#### 参数  
 `RuntimeClassTypeT`  
 指定一个或多个 [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) 枚举数的字段。  
  
## 备注  
 对 `QueryInterface` 运算和获取接口 ID 的帮助器方法。  
  
## 成员  
  
## 继承层次结构  
 `RuntimeClassBaseT`  
  
## 要求  
 **头文件：**implements.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [Reference \(Windows Runtime Library\)](http://msdn.microsoft.com/zh-cn/00000000-0000-0000-0000-000000000000)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)