---
title: "_com_ptr_t 提取器 | Microsoft Docs"
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
  - "_com_ptr_t::operatorInterface&"
  - "operatorInterface*"
  - "operatorInterface&"
  - "_com_ptr_t::operatorbool"
  - "_com_ptr_t.operator->"
  - "_com_ptr_t.operator*"
  - "_com_ptr_t::operator->"
  - "_com_ptr_t::operator*"
  - "_com_ptr_t.operatorInterface&"
  - "_com_ptr_t.operatorbool"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "& 运算符, 具有特定对象"
  - "* 运算符, 具有特定对象"
  - "-> 运算符, 具有特定对象"
  - "提取器"
  - "提取器, _com_ptr_t 类"
  - "运算符 *"
  - "运算符 bool"
  - "运算符 Interface&"
  - "运算符 Interface*"
  - "operator&"
  - "operator*"
  - "operator->"
ms.assetid: 194b9e0e-123c-49ff-a187-0a7fcd68145a
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_ptr_t 提取器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 提取封装的 COM 接口指针。  
  
## 语法  
  
```  
  
      operator Interface*( ) const throw( );   
operator Interface&( ) const;   
Interface& operator*( ) const;   
Interface* operator->( ) const;   
Interface** operator&( ) throw( );   
operator bool( ) const throw( );  
```  
  
## 备注  
  
-   **operator Interface\*** 返回封装的接口指针，这可能为 **NULL**。  
  
-   **operator Interface&** 返回对封装的接口指针的引用，并发布错误（如果指针为 **NULL**）。  
  
-   **operator\*** 允许智能指针对象在取消引用时充当实际封装的接口。  
  
-   **operator\-\>** 允许智能指针对象在取消引用时充当实际封装的接口。  
  
-   **operator&** 释放所有封装的接口指针，将其替换为 **NULL**，并返回封装的指针的地址。  这允许智能指针通过寻址传递到拥有 **out** 参数的函数，它通过该参数返回接口指针。  
  
-   **operator bool** 允许智能指针对象用于一个条件表达式中。  如果该指针不为 **NULL**，则此运算符返回 **true**。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_com\_ptr\_t 类](../cpp/com-ptr-t-class.md)