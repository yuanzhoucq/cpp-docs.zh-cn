---
title: "_variant_t 关系运算符 | Microsoft Docs"
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
  - "_variant_t::operator=="
  - "_variant_t.operator!="
  - "_variant_t::operator!="
  - "_variant_t.operator=="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "!= 运算符"
  - "== 运算符, 具有特定的 Visual C++ 对象"
  - "运算符 !=, 关系运算符"
  - "运算符 !=, 变量"
  - "运算符 ==, 变量"
  - "operator!=, 关系运算符"
  - "operator!=, 变量"
  - "operator==, 变量"
  - "关系运算符, _variant_t 类"
ms.assetid: 141bacb8-41a2-44dd-b3c0-4ad1f884f4ea
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _variant_t 关系运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 比较两个 `_variant_t` 对象是否相等。  
  
## 语法  
  
```  
  
      bool operator==(  
   const VARIANT& varSrc   
) const;  
bool operator==(  
   const VARIANT* pSrc   
) const;  
bool operator!=(  
   const VARIANT& varSrc   
) const;  
bool operator!=(  
   const VARIANT* pSrc   
) const;  
```  
  
#### 参数  
 *varSrc*  
 与 `_variant_t` 对象进行比较的 **VARIANT**。  
  
 `pSrc`  
 指向将与 `_variant_t` 对象进行比较的 **VARIANT** 的指针。  
  
## 返回值  
 如果比较保留，则返回 **true**；否则，返回 **false**。  
  
## 备注  
 比较 `_variant_t` 对象与 **VARIANT** 以测试它们是否相等。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_variant\_t 类](../cpp/variant-t-class.md)