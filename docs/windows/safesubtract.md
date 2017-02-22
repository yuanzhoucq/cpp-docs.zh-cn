---
title: "SafeSubtract | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "SafeSubtract"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SafeSubtract 函数"
ms.assetid: c2712ddc-173f-46a1-b09c-e7ebbd9e68b2
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 5
---
# SafeSubtract
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

增加两个数字。防止溢出的方法。  
  
## 语法  
  
```  
template<typename T, typename U>  
inline bool SafeSubtract (  
   T t,  
   U u,  
   T& result  
) throw ();  
```  
  
#### 参数  
 \[in\] `t`  
 将减法的第一个元素。  这必须是类型 T。  
  
 \[in\] `u`  
 要从中减去的数字从 `t`。  这必须为类型 U。  
  
 \[out\] `result`  
 参数 `SafeSubtract` 存储结果的地方。  
  
## 返回值  
 `true`，如果未发生错误；`false`，如果出错。  
  
## 备注  
 此方法为 [SafeInt 库](../windows/safeint-library.md) 的一部分以及一个减法运算设计，而不会创建的实例。[SafeInt 类](../windows/safeint-class.md)  
  
> [!NOTE]
>  此方法，如果必须保护时，才应使用个数学运算。  如果存在多个操作，应该使用 `SafeInt` 类 \(而非调用各个独立函数。  
  
 有关类型 U 和 T 模板的更多信息，请参见 [SafeInt 函数](../windows/safeint-functions.md)。  
  
## 要求  
 **页眉：** safeint.h  
  
 **命名空间：** Microsoft::Utilities  
  
## 请参阅  
 [SafeInt 函数](../windows/safeint-functions.md)   
 [SafeInt 库](../windows/safeint-library.md)   
 [SafeInt 类](../windows/safeint-class.md)   
 [SafeAdd](../windows/safeadd.md)