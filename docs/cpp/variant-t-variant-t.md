---
title: _variant_t::_variant_t |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::_variant_t
dev_langs:
- C++
helpviewer_keywords:
- _variant_t class [C++], constructor
- _variant_t method [C++]
ms.assetid: a50e5b33-d4c6-4a26-8e7e-a0a25fd9895b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 95b0931438afe8ff151d3c9f6c4727013df79478
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209337"
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
 要复制到新的 `VARIANT` 对象中的 `_variant_t` 对象。  
  
 *pVarSrc*  
 指向`VARIANT`对象复制到新`_variant_t`对象。  
  
 *var_t_Src*  
 要复制到新的 `_variant_t` 对象中的 `_variant_t` 对象。  
  
 *fCopy*  
 如果**false**，提供`VARIANT`对象附加到新`_variant_t`对象而无需进行的新副本`VariantCopy`。  
  
 *ISrc sSrc*  
 要复制到新的 `_variant_t` 对象中的整数值。  
  
 *vtSrc*  
 `VARTYPE`新`_variant_t`对象。  
  
 *fltSrc, dblSrc*  
 要复制到新的 `_variant_t` 对象中的数值。  
  
 *cySrc*  
 要复制到新的 `CY` 对象中的 `_variant_t` 对象。  
  
 *bstrSrc*  
 要复制到新的 `_bstr_t` 对象中的 `_variant_t` 对象。  
  
 *strSrc wstrSrc*  
 要复制到新的 `_variant_t` 对象中的字符串。  
  
 *bSrc*  
 一个**bool**要复制到新值`_variant_t`对象。  
  
 *pIUknownSrc*  
 指向 VT_UNKNOWN 对象封装到新的 COM 接口指针`_variant_t`对象。  
  
 *pDispSrc*  
 指向 VT_DISPATCH 对象封装到新的 COM 接口指针`_variant_t`对象。  
  
 *decSrc*  
 要复制到新的 `DECIMAL` 对象中的 `_variant_t` 值。  
  
 *bSrc*  
 要复制到新的 `BYTE` 对象中的 `_variant_t` 值。  
  
 *cSrc*  
 一个**char**要复制到新值`_variant_t`对象。  
  
 *usSrc*  
 一个**unsigned short**要复制到新值`_variant_t`对象。  
  
 *ulSrc*  
 一个**无符号长**要复制到新值`_variant_t`对象。  
  
 *iSrc*  
 **Int**要复制到新值`_variant_t`对象。  
  
 *uiSrc*  
 **无符号的 int**要复制到新值`_variant_t`对象。  
  
 *i8Src*  
 **__Int64**要复制到新值`_variant_t`对象。  
  
 *ui8Src*  
 **Unsigned 的 __int64**要复制到新值`_variant_t`对象。  
  
## <a name="remarks"></a>备注  
  
-   **_variant_t （)** 构造一个空`_variant_t`对象， `VT_EMPTY`。  
  
-   **_variant_t (VARIANT &***varSrc***)** 构造`_variant_t`对象的副本`VARIANT`对象。     变体类型将保留。  
  
-   **_variant_t (VARIANT**<strong>\*</strong>*pVarSrc***)** 构造`_variant_t`对象的副本`VARIANT`对象。     变体类型将保留。  
  
-   **_variant_t (_variant_t &***var_t_Src***)** 构造`_variant_t`从另一个对象`_variant_t`对象。     变体类型将保留。  
  
-   **_variant_t (VARIANT &***varSrc* **，bool**`fCopy`**)** 构造`_variant_t`从现有对象`VARIANT`对象。       如果*fCopy*是**false**，则**变体**对象附加到新对象，而无需进行复制。  
  
-   **_variant_t (short***sSrc* **，VARTYPE**`vtSrc`**= VT_I2)** 构造`_variant_t`从VT_I2或VT_BOOL类型的对象**短**整数值。       任何其他`VARTYPE`导致 E_INVALIDARG 错误。  
  
-   **_variant_t (long** `lSrc` **，VARTYPE**`vtSrc`**= VT_I4)** 构造`_variant_t`对象的类型为 VT_I4、 VT_BOOL 或从 VT_ERROR**长**整数值。       任何其他`VARTYPE`导致 E_INVALIDARG 错误。  
  
-   **_variant_t (float**`fltSrc`**)** 构造`_variant_t`从 VT_R4 类型的对象**float**数字值。      
  
-   **_variant_t (double** `dblSrc` **，VARTYPE**`vtSrc`**= VT_R8)** 构造`_variant_t`VT_R8 或从 VT_DATE 类型的对象**双**数字值。       任何其他`VARTYPE`导致 E_INVALIDARG 错误。  
  
-   **_variant_t (CY &**`cySrc`**)** 构造`_variant_t`object 类型的从 VT_CY`CY`对象。      
  
-   **_variant_t (_bstr_t &**`bstrSrc`**)** 构造`_variant_t`的对象类型 VT_BSTR 从`_bstr_t`对象。     分配新的 `BSTR`。  
  
-   **_variant_t (wchar_t** <strong>\*</strong> *wstrSrc***)** 构造`_variant_t`类型 VT_BSTR 从 Unicode 字符串的对象。   分配新的 `BSTR`。  
  
-   **_variant_t (char**<strong>\*</strong>`strSrc`**)** 构造`_variant_t`VT_BSTR 类型从字符串的对象。     分配新的 `BSTR`。  
  
-   **_variant_t (bool**`bSrc`**)** 构造`_variant_t`object 类型的从 VT_BOOL **bool**值。      
  
-   **_variant_t (IUnknown** <strong>\*</strong> `pIUknownSrc` **，bool**`fAddRef`**= true)** 构造`_variant_t`类型的对象从 COM 接口指针 VT_UNKNOWN。       如果`fAddRef`是**true**，然后`AddRef`来匹配对的调用提供的接口指针上调用`Release`，将发生时`_variant_t`对象被销毁。 它将由您来调用`Release`上提供的接口指针。 如果`fAddRef`是**false**，此构造函数使用提供的接口指针的所有权; 不调用`Release`上提供的接口指针。  
  
-   **_variant_t (IDispatch** <strong>\*</strong> `pDispSrc` **，bool**`fAddRef`**= true)** 构造`_variant_t`的对象键入 VT_DISPATCH 从 COM 接口指针。       如果`fAddRef`是**true**，然后`AddRef`来匹配对的调用提供的接口指针上调用`Release`，将发生时`_variant_t`对象被销毁。 它将由您来调用`Release`上提供的接口指针。 如果`fAddRef`是**false**，此构造函数使用提供的接口指针的所有权; 不调用`Release`上提供的接口指针。  
  
-   **_variant_t (十进制 &**`decSrc`**)** 构造`_variant_t`object 类型的从 VT_DECIMAL`DECIMAL`值。      
  
-   **_variant_t (BYTE**`bSrc`**)** 构造`_variant_t`类型的对象`VT_UI1`从`BYTE`值。      
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [_variant_t 类](../cpp/variant-t-class.md)