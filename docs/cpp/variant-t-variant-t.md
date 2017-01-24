---
title: "_variant_t::_variant_t | Microsoft Docs"
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
  - "_variant_t::_variant_t"
  - "_variant_t._variant_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_variant_t 类, 构造函数"
  - "_variant_t 方法"
ms.assetid: a50e5b33-d4c6-4a26-8e7e-a0a25fd9895b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _variant_t::_variant_t
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 构造 `_variant_t` 对象。  
  
## 语法  
  
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
  
#### 参数  
 *varSrc*  
 要复制到新 `_variant_t` 对象中的 **VARIANT** 对象。  
  
 *pVarSrc*  
 指向要复制到新的 `_variant_t` 对象中的 **VARIANT** 对象的指针。  
  
 *var\_t\_Src*  
 要复制到新的 `_variant_t` 对象中的 `_variant_t` 对象。  
  
 `fCopy`  
 如果为 false，则提供的 **VARIANT** 对象将附加到新的 `_variant_t` 对象中，而无需通过 **VariantCopy** 创建新副本。  
  
 *ISrc, sSrc*  
 要复制到新的 `_variant_t` 对象中的整数值。  
  
 `vtSrc`  
 新的 `_variant_t` 对象的 **VARTYPE**。  
  
 *fltSrc, dblSrc*  
 要复制到新的 `_variant_t` 对象中的数值。  
  
 `cySrc`  
 要复制到新的 `_variant_t` 对象中的 **CY** 对象。  
  
 `bstrSrc`  
 要复制到新的 `_bstr_t` 对象中的 `_variant_t` 对象。  
  
 *strSrc, wstrSrc*  
 要复制到新的 `_variant_t` 对象中的字符串。  
  
 `bSrc`  
 要复制到新的 `bool` 对象中的 `_variant_t` 值。  
  
 `pIUknownSrc`  
 指向要封装到新的 `_variant_t` 对象中的 **VT\_UNKNOWN** 对象的 COM 接口指针。  
  
 `pDispSrc`  
 指向要封装到新的 `_variant_t` 对象中的 **VT\_DISPATCH** 对象的 COM 接口指针。  
  
 `decSrc`  
 要复制到新的 `_variant_t` 对象中的 **DECIMAL** 值。  
  
 `bSrc`  
 要复制到新的 `_variant_t` 对象中的 **BYTE** 值。  
  
 `cSrc`  
 要复制到新的 `char` 对象中的 `_variant_t` 值。  
  
 *usSrc*  
 要复制到新的 `_variant_t` 对象中的 **unsigned short** 值。  
  
 *ulSrc*  
 要复制到新的 `unsigned long` 对象中的 `_variant_t` 值。  
  
 `iSrc`  
 要复制到新的 `int` 对象中的 `_variant_t` 值。  
  
 *uiSrc*  
 要复制到新的 `unsigned int` 对象中的 `_variant_t` 值。  
  
 *i8Src*  
 要复制到新的 `_variant_t` 对象中的 \_\_**int64** 值。  
  
 *ui8Src*  
 要复制到新的 `_variant_t`对象中的 **unsigned \_\_int64** 值。  
  
## 备注  
  
-   **\_variant\_t\( \)** 构造一个空的 `_variant_t` 对象 `VT_EMPTY`。  
  
-   **\_variant\_t\( VARIANT&**  *varSrc*  **\)** 从 **VARIANT** 对象的副本中构造一个 `_variant_t` 对象。  变体类型将保留。  
  
-   **\_variant\_t\( VARIANT\***  *pVarSrc*  **\)** 从 **VARIANT** 对象的副本中构造一个 `_variant_t` 对象。  变体类型将保留。  
  
-   **\_variant\_t\( \_variant\_t&**  *var\_t\_Src*  **\)** 从另一个 `_variant_t` 对象中构造一个 `_variant_t` 对象。  变体类型将保留。  
  
-   **\_variant\_t\( VARIANT&**  *varSrc* **, bool**  `fCopy`  **\)** 从现有 **VARIANT** 对象中构造一个 `_variant_t` 对象。  如果 `fCopy` 为 **false**，则 **VARIANT** 对象将附加到新对象中，而无需创建副本。  
  
-   **\_variant\_t\( short**  *sSrc* **, VARTYPE**  `vtSrc`  **\= VT\_I2 \)** 从 **short** 整数值构造一个类型为 `VT_I2` 或 `VT_BOOL` 的 `_variant_t` 对象。  任何其他 **VARTYPE** 都会导致 `E_INVALIDARG` 错误。  
  
-   **\_variant\_t\( long**  `lSrc` **, VARTYPE**  `vtSrc`  **\= VT\_I4 \)** 从 **long** 整数值构造一个类型为 `VT_I4`、`VT_BOOL` 或 `VT_ERROR` 的 `_variant_t` 对象。  任何其他 **VARTYPE** 都会导致 `E_INVALIDARG` 错误。  
  
-   **\_variant\_t\( float**  `fltSrc`  **\)** 从 **float** 数值构造一个 `VT_R4` 类型的 `_variant_t` 对象。  
  
-   **\_variant\_t\( double**  `dblSrc` **, VARTYPE**  `vtSrc`  **\= VT\_R8 \)** 从 **double** 数值构造一个 `VT_R8` 或 `VT_DATE` 类型的 `_variant_t` 对象。  任何其他 **VARTYPE** 都会导致 `E_INVALIDARG` 错误。  
  
-   **\_variant\_t\( CY&**  `cySrc`  **\)** 从 **CY** 对象构造一个 `VT_CY` 类型的 `_variant_t` 对象。  
  
-   **\_variant\_t\( \_bstr\_t&**  `bstrSrc`  **\)** 从 `_bstr_t` 对象构造一个 `VT_BSTR` 类型的 `_variant_t` 对象。  分配新的 `BSTR`。  
  
-   **\_variant\_t\( wchar\_t \*** *wstrSrc*  **\)** 从 Unicode 字符串构造一个 `VT_BSTR` 类型的 `_variant_t` 对象。  分配新的 `BSTR`。  
  
-   **\_variant\_t\( char\***  `strSrc`  **\)** 从字符串构造一个 `VT_BSTR` 类型的 `_variant_t` 对象。  分配新的 `BSTR`。  
  
-   **\_variant\_t\( bool**  `bSrc`  **\)** 从 `bool` 值构造一个 `VT_BOOL` 类型的 `_variant_t` 对象。  
  
-   **\_variant\_t\( IUnknown\***  `pIUknownSrc` **, bool**  `fAddRef`  **\= true \)** 从 COM 接口指针构造一个 **VT\_UNKNOWN** 类型的 `_variant_t` 对象。  如果 `fAddRef` 为 **true**，则在提供的接口指针上调用 `AddRef` 以匹配将在 `_variant_t` 对象被销毁时发生的对 **Release** 的调用。  由您来在提供的接口指针上调用 **Release**。  如果 `fAddRef` 为 **false**，则此构造函数将获得提供的接口指针的所有权；不在提供的接口指针上调用 **Release**。  
  
-   **\_variant\_t\( IDispatch\***  `pDispSrc` **, bool**  `fAddRef`  **\= true \)** 从 COM 接口指针构造一个 **VT\_DISPATCH** 类型的 `_variant_t` 对象。  如果 `fAddRef` 为 **true**，则在提供的接口指针上调用 `AddRef` 以匹配将在 `_variant_t` 对象被销毁时发生的对 **Release** 的调用。  由您来在提供的接口指针上调用 **Release**。  如果 **fAddRef** 为 false，则此构造函数将获得提供的接口指针的所有权；不在提供的接口指针上调用 **Release**。  
  
-   **\_variant\_t\( DECIMAL&**  `decSrc`  **\)** 从 **DECIMAL** 值构造一个 **VT\_DECIMAL** 类型的 `_variant_t` 对象。  
  
-   **\_variant\_t\( BYTE**  `bSrc`  **\)** 从 **BYTE** 值构造一个 `VT_UI1` 类型的 `_variant_t` 对象。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_variant\_t 类](../cpp/variant-t-class.md)