---
title: "_bstr_t::operator = | Microsoft Docs"
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
  - "_bstr_t::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "= 运算符, 具有特定的 Visual C++ 对象"
  - "运算符 =, bstr"
  - "operator=, bstr"
ms.assetid: fb31bb1b-ce29-4388-b5fd-8dac830cf18a
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _bstr_t::operator =
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 将新值赋给现有 `_bstr_t` 对象。  
  
## 语法  
  
```  
  
      _bstr_t& operator=(  
   const _bstr_t& s1   
) throw ( );  
_bstr_t& operator=(  
   const char* s2   
);  
_bstr_t& operator=(  
   const wchar_t* s3   
);  
_bstr_t& operator=(  
   const _variant_t& var   
);  
```  
  
#### 参数  
 *s1*  
 将分配给现有 `_bstr_t` 对象的 `_bstr_t` 对象。  
  
 *s2*  
 将分配给现有 `_bstr_t` 对象的多字节字符串。  
  
 `s3`  
 将分配给现有 `_bstr_t` 对象的 Unicode 字符串。  
  
 `var`  
 将分配给现有 `_bstr_t` 对象的 `_variant_t` 对象。  
  
 **结束 Microsoft 专用**  
  
## 示例  
 有关使用 `operator=` 的示例，请参阅 [\_bstr\_t::Assign](../cpp/bstr-t-assign.md)。  
  
## 请参阅  
 [\_bstr\_t 类](../cpp/bstr-t-class.md)