---
title: "SafeLessThan | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "SafeLessThan"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SafeLessThan 函数"
ms.assetid: 9d85bc0d-8d94-4d59-9b72-ef3c63a120a0
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 6
---
# SafeLessThan
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

确定一个值是否小于另一个值  
  
## 语法  
  
```  
template<typename T, typename U>  
inline bool SafeLessThan (  
   const T t,  
   const U u  
) throw ();  
```  
  
#### 参数  
 \[in\] `t`  
 第一个数字。  此类型必须为 T 类型。  
  
 \[in\] `u`  
 第二个数。  此类型必须为 U 类型。  
  
## 返回值  
 如果 `t` 小于 `u`，则为 `true`；否则为 `false`。  
  
## 备注  
 因为这使您能够比较两种不同类型的数字，`SafeLessThan`增强了标准比较运算符。  
  
 此方法为 [SafeInt 库](../windows/safeint-library.md) 的一部分以及设计用于单独的比较操作符，而不会创建[SafeInt 类](../windows/safeint-class.md) 的实例。  
  
> [!NOTE]
>  此方法仅当必须保护单个数学操作时使用。  如果存在多个操作，应该使用 `SafeInt` 类而非调用各个独立函数。  
  
 有关T 和 U 类型的模板的详细信息，请参阅 [SafeInt 函数](../windows/safeint-functions.md)。  
  
## 要求  
 **头文件:** safeint.h  
  
 **Namespace:** Microsoft::Utilities  
  
## 请参阅  
 [SafeInt 函数](../windows/safeint-functions.md)   
 [SafeInt 库](../windows/safeint-library.md)   
 [SafeInt 类](../windows/safeint-class.md)   
 [SafeLessThanEquals](../windows/safelessthanequals.md)   
 [SafeGreaterThan](../windows/safegreaterthan.md)   
 [SafeGreaterThanEquals](../windows/safegreaterthanequals.md)