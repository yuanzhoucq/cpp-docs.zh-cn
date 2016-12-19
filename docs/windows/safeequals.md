---
title: "SafeEquals | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "SafeEquals"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SafeEquals 函数"
ms.assetid: 6019627d-f170-413b-9abd-2b5b34396a72
caps.latest.revision: 6
caps.handback.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# SafeEquals
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

比较两个数字以确定它们是否相等。  
  
## 语法  
  
```  
template<typename T, typename U>  
inline bool SafeEquals (  
   const T t,  
   const U u  
) throw ();  
```  
  
#### 参数  
 \[in\] `t`  
 要比较的第一个数字。  此类型必须为 T 类型。  
  
 \[in\] `u`  
 要比较的第二个数字。  此类型必须为 U 类型。  
  
## 返回值  
 如果 `t` 和 `u` 相等，则为 `true`；否则为 `false`。  
  
## 备注  
 因为 `SafeEquals` 使您能够比较两种不同类型的数字，方法提高了 `==`。  
  
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
 [SafeNotEquals](../windows/safenotequals.md)