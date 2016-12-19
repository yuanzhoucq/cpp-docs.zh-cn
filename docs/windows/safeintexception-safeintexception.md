---
title: "SafeIntException::SafeIntException | Microsoft Docs"
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
  - "SafeIntException"
  - "SafeIntException.SafeIntException"
  - "SafeIntException::SafeIntException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SafeIntException, 构造函数"
ms.assetid: 8e5a0c24-a56b-4c80-9ee8-876604b1e7dc
caps.latest.revision: 6
caps.handback.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# SafeIntException::SafeIntException
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

创建一个 `SafeIntException` 对象。  
  
## 语法  
  
```  
SafeIntException();  
  
SafeIntException(  
   SafeIntError code  
);  
```  
  
#### 参数  
 \[in\] `code`  
 描述错误的一个计算为值。  
  
## 备注  
 `code` 的可能值 Safeint.h 文件中定义。  为方便起见，可能值还此处列出。  
  
-   `SafeIntNoError`  
  
-   `SafeIntArithmeticOverflow`  
  
-   `SafeIntDivideByZero`  
  
## 要求  
 **Header:** safeint.h  
  
 **命名空间：** msl::utilities  
  
## 请参阅  
 [SafeInt 库](../windows/safeint-library.md)   
 [SafeIntException 类](../windows/safeintexception-class.md)   
 [SafeInt 类](../windows/safeint-class.md)