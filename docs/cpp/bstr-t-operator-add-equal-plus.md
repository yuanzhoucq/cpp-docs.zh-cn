---
title: "_bstr_t::operator +=, + | Microsoft Docs"
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
  - "_bstr_t::operator+"
  - "_bstr_t::operator+="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "+ 运算符, _bstr_t 对象"
  - "+= 运算符, 追加字符串"
ms.assetid: d28316ce-c2c8-4a38-bdb3-44fa4e582c44
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _bstr_t::operator +=, +
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 将字符追加到 `_bstr_t` 对象的结尾或串联两个字符串。  
  
## 语法  
  
```  
  
      _bstr_t& operator+=(  
   const _bstr_t& s1   
);  
_bstr_t operator+(  
   const _bstr_t& s1   
);  
friend _bstr_t operator+(  
   const char* s2,  
   const _bstr_t& s1   
);  
friend _bstr_t operator+(  
   const wchar_t* s3,  
   const _bstr_t& s1   
);  
```  
  
#### 参数  
 *s1*  
 一个 `_bstr_t` 对象。  
  
 *s2*  
 多字节字符串。  
  
 `s3`  
 一个 Unicode 字符串。  
  
## 备注  
 以下运算符将执行字符串串联：  
  
-   **operator\+\=\(**  *s1*  **\)** 将 *s1* 的已封装 `BSTR` 中的字符追加到此对象的已封装 `BSTR` 的末尾。  
  
-   **operator\+\(**  *s1*  **\)** 返回通过将此对象的 `BSTR` 与 *s1* 的对应项串联构成的新 `_bstr_t`。  
  
-   **operator\+\(**  *s2*  **&#124;**  *s1*  **\)** 返回通过将多字节字符串 *s2*（已转换为 Unicode）与 *s1* 中封装的 `BSTR` 串联构成的新 `_bstr_t`。  
  
-   **operator\+\(**  `s3` **,**  *s1*  **\)** 返回通过将 Unicode 字符串 `s3` 与 *s1* 中封装的 `BSTR` 串联构成的新 `_bstr_t`。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_bstr\_t 类](../cpp/bstr-t-class.md)