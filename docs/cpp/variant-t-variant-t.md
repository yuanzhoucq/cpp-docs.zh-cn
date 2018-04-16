---
title: _variant_t::_variant_t | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _variant_t::_variant_t
dev_langs:
- C++
helpviewer_keywords:
- _variant_t class [C++], constructor
- _variant_t method [C++]
ms.assetid: a50e5b33-d4c6-4a26-8e7e-a0a25fd9895b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cd85a54e9f73352894f6575051fe1ea8be0698fb
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2018
---
# <a name="varianttvariantt"></a>_variant_t::_variant_t
**Microsoft 专用**  
  
 构造 `_variant_t` 对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
      _variant_t( ) throw( );  
  
_variant_t(  
   const VARIANT& varSrc   
);  
  
_variant_t(  
   const VARIANT* pVarSrc   
);  
  
_variant_t(  
   const _variant_t& var_t_Src   
);  
  
_variant_t(  
   VARIANT& varSrc,  
   bool fCopy   
);  
  
_variant_t(  
   short sSrc,  
   VARTYPE vtSrc = VT_I2   
);  
  
_variant_t(  
   long lSrc,  
   VARTYPE vtSrc = VT_I4   
);  
  
_variant_t(  
   float fltSrc   
) throw( );  
  
_variant_t(  
   double dblSrc,  
   VARTYPE vtSrc = VT_R8   
);  
  
_variant_t(  
   const CY& cySrc   
) throw( );  
  
_variant_t(  
   const _bstr_t& bstrSrc   
);  
  
_variant_t(  
   const wchar_t *wstrSrc   
);  
  
_variant_t(  
   const char* strSrc   
);  
  
_variant_t(  
   IDispatch* pDispSrc,  
   bool fAddRef = true   
) throw( );  
  
_variant_t(  
   bool bSrc   
) throw( );  
  
_variant_t(  
   IUnknown* pIUknownSrc,  
   bool fAddRef = true   
) throw( );  
  
_variant_t(  
   const DECIMAL& decSrc   
) throw( );  
  
_variant_t(  
   BYTE bSrc   
) throw( );  
  
variant_t(  
   char cSrc  
) throw();  
  
_variant_t(  
   unsigned short usSrc  
) throw();  
  
_variant_t(  
   unsigned long ulSrc  
) throw();  
  
_variant_t(  
   int iSrc  
) throw();  
  
_variant_t(  
   unsigned int uiSrc  
) throw();  
  
_variant_t(  
   __int64 i8Src  
) throw();  
  
_variant_t(  
   unsigned __int64 ui8Src  
) throw();  
```  
  
#### <a name="parameters"></a>参数  
 *varSrc*  
 A **VARIANT**要复制到新对象`_variant_t`对象。  
  
 *pVarSrc*  
 指向**VARIANT**要复制到新对象`_variant_t`对象。  
  
 *var_t_Src*  
 要复制到新的 `_variant_t` 对象中的 `_variant_t` 对象。  
  
 `fCopy`  
 如果为 false，提供**VARIANT**对象附加到新`_variant_t`对象而不创建新的副本通过**VariantCopy**。  
  
 *ISrc, sSrc*  
 要复制到新的 `_variant_t` 对象中的整数值。  
  
 `vtSrc`  
 **VARTYPE**新`_variant_t`对象。  
  
 *fltSrc, dblSrc*  
 要复制到新的 `_variant_t` 对象中的数值。  
  
 `cySrc`  
 A **CY**要复制到新对象`_variant_t`对象。  
  
 `bstrSrc`  
 要复制到新的 `_bstr_t` 对象中的 `_variant_t` 对象。  
  
 *strSrc, wstrSrc*  
 要复制到新的 `_variant_t` 对象中的字符串。  
  
 `bSrc`  
 要复制到新的 `bool` 对象中的 `_variant_t` 值。  
  
 `pIUknownSrc`  
 COM 接口指针**VT_UNKNOWN**要封装到新对象`_variant_t`对象。  
  
 `pDispSrc`  
 COM 接口指针**VT_DISPATCH**要封装到新对象`_variant_t`对象。  
  
 `decSrc`  
 A**十进制**要复制到新值`_variant_t`对象。  
  
 `bSrc`  
 A**字节**要复制到新值`_variant_t`对象。  
  
 `cSrc`  
 要复制到新的 `char` 对象中的 `_variant_t` 值。  
  
 *usSrc*  
 A**无符号短**要复制到新值`_variant_t`对象。  
  
 *ulSrc*  
 要复制到新的 `unsigned long` 对象中的 `_variant_t` 值。  
  
 `iSrc`  
 要复制到新的 `int` 对象中的 `_variant_t` 值。  
  
 *uiSrc*  
 要复制到新的 `unsigned int` 对象中的 `_variant_t` 值。  
  
 *i8Src*  
 __**Int64**要复制到新值`_variant_t`对象。  
  
 *ui8Src*  
 **Unsigned 的 __int64**要复制到新值`_variant_t`对象。  
  
## <a name="remarks"></a>备注  
  
-   **_variant_t （)**构造一个空`_variant_t`对象， `VT_EMPTY`。  
  
-   **_variant_t (VARIANT &***varSrc***)**构造`_variant_t`对象的副本**VARIANT**对象。     变体类型将保留。  
  
-   **_variant_t (VARIANT\****pVarSrc***)**构造`_variant_t`对象的副本**VARIANT**对象。     变体类型将保留。  
  
-   **_variant_t (_variant_t （& a)***var_t_Src***)**构造`_variant_t`从另一个对象`_variant_t`对象。     变体类型将保留。  
  
-   **_variant_t (VARIANT &***varSrc* **，bool**`fCopy`**)**构造`_variant_t`从现有对象**VARIANT**对象。       如果`fCopy`是**false**、 **VARIANT**对象附加到新的对象，而无需制作的副本。  
  
-   **_variant_t (短***sSrc* **，VARTYPE**`vtSrc`**= VT_I2)**构造`_variant_t`类型的对象`VT_I2`或`VT_BOOL`从**短**整数值。       任何其他**VARTYPE**导致`E_INVALIDARG`错误。  
  
-   **_variant_t (长**`lSrc` **，VARTYPE**`vtSrc`**= VT_I4)**构造`_variant_t`类型的对象`VT_I4`， `VT_BOOL`，或`VT_ERROR`从**长**整数值。       任何其他**VARTYPE**导致`E_INVALIDARG`错误。  
  
-   **_variant_t (float**`fltSrc`**)**构造`_variant_t`类型的对象`VT_R4`从**float**数字值。      
  
-   **_variant_t (double** `dblSrc` **，VARTYPE**`vtSrc`**= VT_R8)**构造`_variant_t`类型的对象`VT_R8`或`VT_DATE`从**double**数字值。       任何其他**VARTYPE**导致`E_INVALIDARG`错误。  
  
-   **_variant_t (CY （& a)**`cySrc`**)**构造`_variant_t`类型的对象`VT_CY`从**CY**对象。      
  
-   **_variant_t (_bstr_t （& a)**`bstrSrc`**)**构造`_variant_t`类型的对象`VT_BSTR`从`_bstr_t`对象。     分配新的 `BSTR`。  
  
-   **_variant_t (wchar_t \***  *wstrSrc***)**构造`_variant_t`类型的对象`VT_BSTR`从 Unicode 字符串。   分配新的 `BSTR`。  
  
-   **_variant_t (char\***`strSrc`**)**构造`_variant_t`类型的对象`VT_BSTR`从字符串。     分配新的 `BSTR`。  
  
-   **_variant_t (bool**`bSrc`**)**构造`_variant_t`类型的对象`VT_BOOL`从`bool`值。      
  
-   **_variant_t (IUnknown\***  `pIUknownSrc` **，bool**`fAddRef`**= true)**构造`_variant_t`类型的对象**VT_UNKNOWN**从 COM 接口指针。       如果`fAddRef`是**true**，然后`AddRef`对提供的接口的指针来匹配到调用调用**版本**将发生时`_variant_t`对象被销毁。 它将由您来调用**版本**上提供的接口指针。 如果`fAddRef`是**false**，此构造函数将提供的接口指针的所有权; 不调用**版本**上提供的接口指针。  
  
-   **_variant_t (IDispatch\***  `pDispSrc` **，bool**`fAddRef`**= true)**构造`_variant_t`类型的对象**VT_DISPATCH**从 COM 接口指针。       如果`fAddRef`是**true**，然后`AddRef`对提供的接口的指针来匹配到调用调用**版本**将发生时`_variant_t`对象被销毁。 它将由您来调用**版本**上提供的接口指针。 如果**fAddRef**是 false，此构造函数将提供的接口指针的所有权; 不调用**版本**上提供的接口指针。  
  
-   **_variant_t (十进制 （& a)**`decSrc`**)**构造`_variant_t`类型的对象**VT_DECIMAL**从**十进制**值。      
  
-   **_variant_t (字节**`bSrc`**)**构造`_variant_t`类型的对象`VT_UI1`从**字节**值。      
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [_variant_t 类](../cpp/variant-t-class.md)