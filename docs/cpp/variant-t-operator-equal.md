---
title: _variant_t::operator =
ms.date: 11/04/2016
f1_keywords:
- _variant_t::operator=
helpviewer_keywords:
- operator= [C++], variant
- operator = [C++], variant
- = operator [C++], with specific Visual C++ objects
ms.assetid: 77622723-6e49-4dec-9e0f-fa74028f1a3c
ms.openlocfilehash: 402251592a87b723d75fd1b2cd0786be7b17dbfc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187617"
---
# <a name="_variant_toperator-"></a>_variant_t::operator =

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

- **operator = （** *varSrc* **）** 向 `_variant_t` 对象分配现有 `VARIANT`。

- **operator = （** *pVarSrc* **）** 向 `_variant_t` 对象分配现有 `VARIANT`。

- **operator = （** *var_t_Src* **）** 向 `_variant_t` 对象分配现有的 `_variant_t` 对象。

- **operator = （** *sSrc* **）** 向 `_variant_t` 对象分配一个**短**整型值。

- **operator = （** `lSrc` **）** 向 `_variant_t` 对象分配一个**长**整型值。

- **operator = （** *fltSrc* **）** 向 `_variant_t` 对象分配一个**浮点**数字值。

- **operator = （** *dblSrc* **）** 向 `_variant_t` 对象分配一个**双精度**数字值。

- **operator = （**  *cySrc*  **）** 将 `CY` 对象分配到 `_variant_t` 对象。

- **operator = （**  *bstrSrc*  **）** 将 `BSTR` 对象分配到 `_variant_t` 对象。

- **operator = （**  *wstrSrc*  **）** 向 `_variant_t` 对象分配一个 Unicode 字符串。

- **operator = （** `strSrc` **）** 将多字节字符串分配给 `_variant_t` 的对象。

- **operator = （** `bSrc` **）** 向 `_variant_t` 对象分配一个**bool**值。

- **operator = （**  *pDispSrc*  **）** 将 `VT_DISPATCH` 对象分配到 `_variant_t` 对象。

- **operator = （**  *pIUnknownSrc*  **）** 将 `VT_UNKNOWN` 对象分配到 `_variant_t` 对象。

- **operator = （** *decSrc* **）** 向 `_variant_t` 对象分配 `DECIMAL` 值。

- **operator = （** `bSrc` **）** 向 `_variant_t` 对象分配 `BYTE` 值。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[_variant_t 类](../cpp/variant-t-class.md)
