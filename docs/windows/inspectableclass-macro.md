---
title: "InspectableClass 宏 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::InspectableClass"
dev_langs: 
  - "C++"
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# InspectableClass 宏
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

设置运行时类名和信任级别。  
  
## 语法  
  
```cpp  
  
InspectableClass(  
   runtimeClassName,   
   trustLevel)  
  
```  
  
#### 参数  
 `runtimeClassName`  
 运行时类的文本全名。  
  
 `trustLevel`  
 [TrustLevel](http://msdn.microsoft.com/library/br224625.aspx)（信任级别）枚举值之一。  
  
## 备注  
 `InspectableClass` 宏只能与 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]类型一起使用。  
  
## 要求  
 **头文件：**implements.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [RuntimeClass 类](../windows/runtimeclass-class.md)