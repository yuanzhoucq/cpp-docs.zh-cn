---
title: "identity 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::identity"
  - "utility/std::identity"
  - "identity"
  - "std.identity"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "identity 类"
  - "identity 结构"
ms.assetid: 990756fd-7969-4b39-ad7e-0878e8dac8fd
caps.latest.revision: 15
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# identity 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

提供了一种类型参数定义为模板的结构。  
  
## 语法  
  
```  
template<class Type>  
   struct identity {  
      typedef Type type;  
      Type operator()(const Type& _Left) const;  
   };  
```  
  
#### 参数  
  
|参数|说明|  
|--------|--------|  
|`_Left`|标识的值。|  
  
## 备注  
 类包含公共类型定义 `type`，与模板参数类型。  当模板函数 [forward](../Topic/forward.md) 一同用于确保函数参数的所需类型。  
  
 为了与早期代码的兼容性，类还定义返回参数 `_Left`的恒等函数 `operator()`。  
  
## 要求  
 **页眉：** \<实用工具\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [\<utility\>](../standard-library/utility.md)