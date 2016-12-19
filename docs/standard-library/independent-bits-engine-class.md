---
title: "independent_bits_engine 类 | Microsoft Docs"
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
  - "std.tr1.independent_bits_engine"
  - "std::tr1::independent_bits_engine"
  - "tr1::independent_bits_engine"
  - "tr1.independent_bits_engine"
  - "independent_bits_engine"
  - "random/std::tr1::independent_bits_engine"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "independent_bits_engine 类"
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
caps.latest.revision: 17
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# independent_bits_engine 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通过再次从其基引擎返回的值中打包位，生成具有指定位数的随机数字序列。  
  
## 语法  
  
```  
template<class Engine, size_t W, class UIntType> class independent_bits_engine;  
```  
  
#### 参数  
 `Engine`  
 基引擎类型。  
  
 `W`  
 **字大小**。  生成的每个数字的大小（以字节为单位）。  **前置条件**：`0 < W ≤ numeric_limits<UIntType>::digits`  
  
 `UIntType`  
 无符号的整数结果类型。  有关可能的类型，请参阅 [\<random\>](../standard-library/random.md)。  
  
## Members  
  
||||  
|-|-|-|  
|`independent_bits_engine::independent_bits_engine`|`independent_bits_engine::base`|`independent_bits_engine::discard`|  
|`independent_bits_engine::operator()`|`independent_bits_engine::base_type`|`independent_bits_engine::seed`|  
  
 有关引擎成员的详细信息，请参阅 [\<random\>](../standard-library/random.md)。  
  
## 备注  
 此模板类描述了*引擎适配器*，该引擎适配器通过再次打包其基引擎返回的值中的位来产生 `W` 位值。  
  
## 要求  
 **标头：**\<random\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<random\>](../standard-library/random.md)