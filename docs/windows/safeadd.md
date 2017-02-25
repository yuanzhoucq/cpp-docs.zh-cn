---
title: "SafeAdd | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "SafeAdd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SafeAdd 函数"
ms.assetid: 3f82b91d-59fe-4ee1-873b-d056182fa8be
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 5
---
# SafeAdd
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

添加两个数字。防止溢出的方法。  
  
## 语法  
  
```  
template<typename T, typename U>  
inline bool SafeAdd (  
   T t,  
   U u,  
   T& result  
) throw ();  
```  
  
#### 参数  
 \[in\] `t`  
 添加第一个数字。  此类型必须为 T 类型。  
  
 \[in\] `u`  
 要相加的第二个数。  此类型必须为 U 类型。  
  
 \[out\] `result`  
 参数 `SafeAdd` 存储结果的地方。  
  
## 返回值  
 如果未发生错误，则为`true`；如果出错，则为`false`。  
  
## 备注  
 此方法为 [SafeInt 库](../windows/safeint-library.md) 的一部分以及一个单添加操作设计，而不会创建[SafeInt 类](../windows/safeint-class.md) 的实例。  
  
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
 [SafeSubtract](../windows/safesubtract.md)