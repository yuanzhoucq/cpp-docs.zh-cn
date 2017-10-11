---
title: "_bstr_t::operator + =，+ |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _bstr_t::operator+
- _bstr_t::operator+=
dev_langs:
- C++
helpviewer_keywords:
- += operator [C++], appending strings
- + operator [C++], _bstr_t objects
ms.assetid: d28316ce-c2c8-4a38-bdb3-44fa4e582c44
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 0ba8936df56359523a76992866642521f899af69
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="bstrtoperator--"></a>_bstr_t::operator +=, +
**Microsoft 专用**  
  
 将字符追加到 `_bstr_t` 对象的结尾或串联两个字符串。  
  
## <a name="syntax"></a>语法  
  
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
  
#### <a name="parameters"></a>参数  
 *s1*  
 一个 `_bstr_t` 对象。  
  
 *s2*  
 多字节字符串。  
  
 `s3`  
 一个 Unicode 字符串。  
  
## <a name="remarks"></a>备注  
 以下运算符将执行字符串串联：  
  
-   **运算符 + = (***s1***)**追加中封装的字符`BSTR`的*s1*到此对象的封装末尾`BSTR`.      
  
-   **operator + (***s1***)**返回新`_bstr_t`，通过串联此对象的格式正确`BSTR`为*s1*。      
  
-   **operator + (***s2***&#124;***s1***)**返回一个新`_bstr_t`，通过串联的多字节字符串形成*s2*，并且被转换为 Unicode，与`BSTR`封装在*s1*。          
  
-   **operator + (** `s3` **，***s1***)**返回一个新`_bstr_t`，通过串联 Unicode 字符串形成`s3`与`BSTR`封装在*s1*。        
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [_bstr_t 类](../cpp/bstr-t-class.md)
