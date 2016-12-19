---
title: "_bstr_t 关系运算符 | Microsoft Docs"
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
  - "_bstr_t::operator>"
  - "_bstr_t::operator=="
  - "_bstr_t::operator>="
  - "_bstr_t::operator!="
  - "_bstr_t::operator<"
  - "_bstr_t::operator<="
  - "_bstr_t::operator!"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "!= 运算符"
  - "< 运算符, 比较特定对象"
  - "<= 运算符, 具有特定对象"
  - "== 运算符, 具有特定的 Visual C++ 对象"
  - "> 运算符, 比较特定对象"
  - ">= 运算符, 比较特定对象"
  - "运算符 !=, 关系运算符"
  - "运算符 <, bstr"
  - "运算符 <=, bstr"
  - "运算符 ==, bstr"
  - "运算符 >, bstr"
  - "运算符 >=, bstr"
  - "operator!=, 关系运算符"
  - "运算符<, bstr"
  - "运算符<=, bstr"
  - "operator==, bstr"
  - "运算符>=, bstr"
  - "关系运算符, _bstr_t 类"
ms.assetid: e153da72-37c3-4d8a-b8eb-730d65da64dd
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _bstr_t 关系运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 比较两个 `_bstr_t` 对象。  
  
## 语法  
  
```  
  
      bool operator!( ) const throw( );   
bool operator==(  
   const _bstr_t& str   
) const throw( );  
bool operator!=(  
   const _bstr_t& str   
) const throw( );  
bool operator<(  
   const _bstr_t& str   
) const throw( );  
bool operator>(  
   const _bstr_t& str   
) const throw( );  
bool operator<=(  
   const _bstr_t& str   
) const throw( );  
bool operator>=(  
   const _bstr_t& str   
) const throw( );  
```  
  
## 备注  
 这些运算符按字典顺序比较两个 `_bstr_t` 对象。  如果该比较保留，运算符将返回 **true**；否则返回 **false**。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_bstr\_t 类](../cpp/bstr-t-class.md)