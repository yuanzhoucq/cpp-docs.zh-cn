---
title: "_variant_t::operator = |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _variant_t::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= [C++], variant
- operator = [C++], variant
- = operator [C++], with specific Visual C++ objects
ms.assetid: 77622723-6e49-4dec-9e0f-fa74028f1a3c
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 850562235442ef8fed4f7b130948a5e92b15a1fb
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="varianttoperator-"></a>_variant_t::operator =
**Microsoft 专用**  
  
## <a name="syntax"></a>语法  
  
```  
  
      _variant_t& operator=(  
   const VARIANT& varSrc   
);  
  
_variant_t& operator=(  
   const VARIANT* pVarSrc   
);  
  
_variant_t& operator=(  
   const _variant_t& var_t_Src   
);  
  
_variant_t& operator=(  
   short sSrc   
);  
  
_variant_t& operator=(  
   long lSrc   
);  
  
_variant_t& operator=(  
   float fltSrc   
);  
  
_variant_t& operator=(  
   double dblSrc   
);  
  
_variant_t& operator=(  
   const CY& cySrc   
);  
  
_variant_t& operator=(  
   const _bstr_t& bstrSrc   
);  
  
_variant_t& operator=(  
   const wchar_t* wstrSrc   
);  
  
_variant_t& operator=(  
   const char* strSrc   
);  
  
_variant_t& operator=(  
   IDispatch* pDispSrc   
);  
  
_variant_t& operator=(  
   bool bSrc   
);  
  
_variant_t& operator=(  
   IUnknown* pSrc   
);  
  
_variant_t& operator=(  
   const DECIMAL& decSrc   
);  
  
_variant_t& operator=(  
   BYTE bSrc   
);  
  
_variant_t& operator=(  
   char cSrc  
);  
  
_variant_t& operator=(  
   unsigned short usSrc  
);  
  
_variant_t& operator=(  
   unsigned long ulSrc  
);  
  
_variant_t& operator=(  
   int iSrc  
);  
  
_variant_t& operator=(  
   unsigned int uiSrc  
);  
  
_variant_t& operator=(  
   __int64 i8Src  
);  
  
_variant_t& operator=(  
   unsigned __int64 ui8Src  
);  
```  
  
## <a name="remarks"></a>备注  
 此运算符将向 `_variant_t` 对象赋予新值：  
  
-   **运算符 = (***varSrc***)**将分配一个现有**VARIANT**到`_variant_t`对象。      
  
-   **运算符 = (***pVarSrc***)**将分配一个现有**VARIANT**到`_variant_t`对象。      
  
-   **运算符 = (***var_t_Src***)**将分配一个现有`_variant_t`对象传递给`_variant_t`对象。      
  
-   **运算符 = (***sSrc***)**分配**短**整数值到`_variant_t`对象。      
  
-   **运算符 = (**`lSrc`**)**分配**长**整数值到`_variant_t`对象。      
  
-   **运算符 = (***fltSrc***)**分配**float**到数值`_variant_t`对象。      
  
-   **运算符 = (***dblSrc***)**分配**double**到数值`_variant_t`对象。      
  
-   **运算符 = (***cySrc***)**分配**CY**对象传递给`_variant_t`对象。      
  
-   **运算符 = (***bstrSrc***)**分配`BSTR`对象传递给`_variant_t`对象。      
  
-   **运算符 = (***wstrSrc***)**将分配到的 Unicode 字符串`_variant_t`对象。      
  
-   **运算符 = (**`strSrc`**)**将分配到的多字节字符串`_variant_t`对象。      
  
-   **运算符 = (** `bSrc` **)**分配`bool`值赋给`_variant_t`对象。    
  
-   **运算符 = (***pDispSrc***)**分配**VT_DISPATCH**对象传递给`_variant_t`对象。      
  
-   **运算符 = (***pIUnknownSrc***)**分配**VT_UNKNOWN**对象传递给`_variant_t`对象。      
  
-   **运算符 = (***decSrc***)**分配**十进制**值赋给`_variant_t`对象。      
  
-   **运算符 = (** `bSrc` **)**分配**字节**值赋给`_variant_t`对象。    
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [_variant_t 类](../cpp/variant-t-class.md)
