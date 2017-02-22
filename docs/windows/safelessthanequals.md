---
title: "SafeLessThanEquals | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "SafeLessThanEquals"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SafeLessThanEquals 函数"
ms.assetid: cbd70526-faf2-4fbc-96a0-b61e8cf5f04a
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 6
---
# SafeLessThanEquals
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

比较两个数。  
  
## 语法  
  
```  
template <typename T, typename U>  
inline bool SafeLessThanEquals (  
   const T t,  
   const U u  
) throw ();  
```  
  
#### 参数  
 \[in\] `t`  
 要比较的第一个数字。  这必须是类型 T。  
  
 \[in\] `u`  
 要比较的第二个数字。  这必须为类型 U。  
  
## 返回值  
 `true`，如果 `t` 小于或等于 `u`;否则为 `false`。  
  
## 备注  
 `SafeLessThanEquals` 通过使您能够比较数字的两种不同类型扩展普通比较运算符。  
  
 此方法为 [SafeInt 库](../windows/safeint-library.md) 的一部分以及单个比较操作设计，而不会创建的实例。[SafeInt 类](../windows/safeint-class.md)  
  
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
 [SafeGreaterThan](../windows/safegreaterthan.md)   
 [SafeLessThan](../windows/safelessthan.md)   
 [SafeGreaterThanEquals](../windows/safegreaterthanequals.md)