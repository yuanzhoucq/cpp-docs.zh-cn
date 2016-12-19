---
title: "RuntimeClassFlags 结构 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::RuntimeClassFlags"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RuntimeClassFlags 结构"
ms.assetid: 7098d605-bd14-4d51-82f4-3def8296a938
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RuntimeClassFlags 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包含 [RuntimeClass](../windows/runtimeclass-class.md)的实例的类型。  
  
## 语法  
  
```  
template <  
   unsigned int flags  
>  
struct RuntimeClassFlags;  
```  
  
#### 参数  
 `flags`  
 一个 [RuntimeClassType 枚举](../windows/runtimeclasstype-enumeration.md) 值。  
  
## 成员  
  
### 公共常量  
  
|名称|说明|  
|--------|--------|  
|[RuntimeClassFlags::value 常量](../windows/runtimeclassflags-value-constant.md)|包含 [RuntimeClassType 枚举](../windows/runtimeclasstype-enumeration.md) 一个值。|  
  
## 继承层次结构  
 `RuntimeClassFlags`  
  
## 要求  
 **头文件：**implements.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [Microsoft::WRL 命名空间](../windows/microsoft-wrl-namespace.md)