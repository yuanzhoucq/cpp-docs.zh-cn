---
title: "SafeCast | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "SafeCast"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SafeCast 函数"
ms.assetid: 55316729-8456-403a-9f96-59d4038f67af
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 7
---
# SafeCast
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将数字类型转换为另一种类型。  
  
## 语法  
  
```  
template<typename T, typename U>  
inline bool SafeCast (  
   const T From,  
   U& To  
);  
```  
  
#### 参数  
 \[in\] `From`  
 要转换的资源号。  此类型必须为 T 类型。  
  
 \[out\] `To`  
 对新数字类型的引用。  此类型必须为 U 类型。  
  
## 返回值  
 如果未发生错误，则为`true`；如果出错，则为`false`。  
  
## 备注  
 此方法为 [SafeInt 库](../windows/safeint-library.md) 的一部分以及一个强制转换操作设计，而不会创建[SafeInt 类](../windows/safeint-class.md) 的实例。  
  
> [!NOTE]
>  此方法仅当必须保护单个操作时使用。  如果存在多个操作，应该使用 `SafeInt` 类而非调用各个独立函数。  
  
 有关T 和 U 类型的模板的详细信息，请参阅 [SafeInt 函数](../windows/safeint-functions.md)。  
  
## 要求  
 **Header:** safeint.h  
  
 **Namespace:** Microsoft::Utilities  
  
## 请参阅  
 [SafeInt 函数](../windows/safeint-functions.md)   
 [SafeInt 库](../windows/safeint-library.md)   
 [SafeInt 类](../windows/safeint-class.md)