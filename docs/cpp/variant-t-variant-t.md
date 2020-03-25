---
title: _variant_t::_variant_t
ms.date: 11/04/2016
f1_keywords:
- _variant_t::_variant_t
helpviewer_keywords:
- _variant_t class [C++], constructor
- _variant_t method [C++]
ms.assetid: a50e5b33-d4c6-4a26-8e7e-a0a25fd9895b
ms.openlocfilehash: fff116ef04967a1887eaa075d92d3ea0283d5427
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187526"
---
# <a name="_variant_t_variant_t"></a>_variant_t::_variant_t

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

#### <a name="parameters"></a>parameters

*varSrc*<br/>
要复制到新的 `VARIANT` 对象中的 `_variant_t` 对象。

*pVarSrc*<br/>
指向要复制到新 `_variant_t` 对象的 `VARIANT` 对象的指针。

*var_t_Src*<br/>
要复制到新的 `_variant_t` 对象中的 `_variant_t` 对象。

*fCopy*<br/>
如果**为 false**，则将提供的 `VARIANT` 对象附加到新的 `_variant_t` 对象，而不 `VariantCopy`创建新的副本。

*ISrc、sSrc*<br/>
要复制到新的 `_variant_t` 对象中的整数值。

*vtSrc*<br/>
新的 `_variant_t` 对象的 `VARTYPE`。

*fltSrc, dblSrc*<br/>
要复制到新的 `_variant_t` 对象中的数值。

*cySrc*<br/>
要复制到新的 `CY` 对象中的 `_variant_t` 对象。

*bstrSrc*<br/>
要复制到新的 `_bstr_t` 对象中的 `_variant_t` 对象。

*strSrc、wstrSrc*<br/>
要复制到新的 `_variant_t` 对象中的字符串。

*bSrc*<br/>
要复制到新 `_variant_t` 对象中的**布尔**值。

*pIUknownSrc*<br/>
指向要封装到新的 `_variant_t` 对象中的 VT_UNKNOWN 对象的 COM 接口指针。

*pDispSrc*<br/>
指向要封装到新的 `_variant_t` 对象中的 VT_DISPATCH 对象的 COM 接口指针。

*decSrc*<br/>
要复制到新的 `DECIMAL` 对象中的 `_variant_t` 值。

*bSrc*<br/>
要复制到新的 `BYTE` 对象中的 `_variant_t` 值。

*cSrc*<br/>
要复制到新 `_variant_t` 对象中的**char**值。

*usSrc*<br/>
要复制到新 `_variant_t` 对象中的**无符号短**值。

*ulSrc*<br/>
要复制到新 `_variant_t` 对象中的**无符号长整型**值。

*iSrc*<br/>
要复制到新 `_variant_t` 对象中的**整数**值。

*uiSrc*<br/>
要复制到新 `_variant_t` 对象中的**无符号整数**值。

*i8Src*<br/>
要复制到新的 `_variant_t` 对象的 **__int64**值。

*ui8Src*<br/>
要复制到新的 `_variant_t` 对象中的**未签名 __int64**值。

## <a name="remarks"></a>备注

- **_variant_t （）** 构造一个空的 `_variant_t` 对象，`VT_EMPTY`。

- **_variant_t （variant &** *varSrc* **）** 构造 `VARIANT` 对象的副本中的 `_variant_t` 对象。 变体类型将保留。

- **_variant_t （variant** <strong>\*</strong> *pVarSrc* **）** 构造 `VARIANT` 对象的副本中的 `_variant_t` 对象。 变体类型将保留。

- **_variant_t （_variant_t &** *var_t_Src* **）** 从另一个 `_variant_t` 对象构造 `_variant_t` 的对象。 变体类型将保留。

- **_variant_t （variant &** *varSrc* **，bool**`fCopy` **）** 构造现有 `VARIANT` 对象的 `_variant_t` 对象。 如果*fCopy*为**False**，则**变量**对象将附加到新的对象，而不创建副本。

- **_variant_t （short***sSrc* **，VARTYPE**`vtSrc` **= VT_I2）** 从**短**整型值构造 VT_I2 或 VT_BOOL 类型的 `_variant_t` 对象。 任何其他 `VARTYPE` 会导致 E_INVALIDARG 错误。

- **_variant_t （long**`lSrc` **，VARTYPE**`vtSrc` **= VT_I4）** 从**长**整数值构造 VT_I4、VT_BOOL 或 VT_ERROR 类型的 `_variant_t` 对象。 任何其他 `VARTYPE` 会导致 E_INVALIDARG 错误。

- **_variant_t （float**`fltSrc` **）** 从**浮点**数值构造 VT_R4 类型的 `_variant_t` 对象。

- **_variant_t （double**`dblSrc` **，VARTYPE**`vtSrc` **= VT_R8）** 构造一个 VT_R8 类型的 `_variant_t` 对象，或从**double**数值 VT_DATE。 任何其他 `VARTYPE` 会导致 E_INVALIDARG 错误。

- **_variant_t （CY &** `cySrc` **）** 从 `CY` 对象构造 VT_CY 类型的 `_variant_t` 对象。

- **_variant_t （_bstr_t &** `bstrSrc` **）** 从 `_bstr_t` 对象构造 VT_BSTR 类型的 `_variant_t` 对象。 分配新的 `BSTR`。

- **_variant_t （wchar_t** <strong>\*</strong> *wstrSrc*  **）** 从 Unicode 字符串构造 VT_BSTR 类型的 `_variant_t` 对象。 分配新的 `BSTR`。

- **_variant_t （char** <strong>\*</strong>`strSrc` **）** 从字符串构造 VT_BSTR 类型的 `_variant_t` 对象。 分配新的 `BSTR`。

- **_variant_t （bool**`bSrc` **）** 从**BOOL**值构造 VT_BOOL 类型的 `_variant_t` 对象。

- **_variant_t （IUnknown** <strong>\*</strong>`pIUknownSrc` **，bool**`fAddRef` **= true）** 从 COM 接口指针构造 VT_UNKNOWN 类型的 `_variant_t` 对象。 如果 `fAddRef` 为**true**，则在提供的接口指针上调用 `AddRef`，以匹配对 `_variant_t` 对象销毁时将发生的 `Release` 的调用。 你需要在提供的接口指针上调用 `Release`。 如果 `fAddRef` 为**false**，则此构造函数将获得提供的接口指针的所有权;不要在提供的接口指针上调用 `Release`。

- **_variant_t （IDispatch** <strong>\*</strong>`pDispSrc` **，bool**`fAddRef` **= true）** 从 COM 接口指针构造 VT_DISPATCH 类型的 `_variant_t` 对象。 如果 `fAddRef` 为**true**，则在提供的接口指针上调用 `AddRef`，以匹配对 `_variant_t` 对象销毁时将发生的 `Release` 的调用。 你需要在提供的接口指针上调用 `Release`。 如果 `fAddRef` 为**false**，则此构造函数将获得提供的接口指针的所有权;不要在提供的接口指针上调用 `Release`。

- **_variant_t （DECIMAL &** `decSrc` **）** 从 `DECIMAL` 值构造 VT_DECIMAL 类型的 `_variant_t` 对象。

- **_variant_t （BYTE**`bSrc` **）** 从 `BYTE` 值构造 `VT_UI1` 类型的 `_variant_t` 对象。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[_variant_t 类](../cpp/variant-t-class.md)
