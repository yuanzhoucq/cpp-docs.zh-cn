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
ms.openlocfilehash: 6a8f31e8db6f5ca5a680dd47b5d5391c84ce5025
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403305"
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

- **运算符 = (***varSrc***)** 将现有`VARIANT`到`_variant_t`对象。

- **运算符 = (***pVarSrc***)** 将现有`VARIANT`到`_variant_t`对象。

- **运算符 = (***var_t_Src***)** 将现有`_variant_t`对象传递给`_variant_t`对象。    

- **运算符 = (***sSrc***)** 分配**短**整数值到`_variant_t`对象。

- **运算符 = (**`lSrc`**)** 分配**长**整数值到`_variant_t`对象。

- **operator=(**  *fltSrc*  **)** Assigns a **float** numerical value to a `_variant_t` object.

- **运算符 = (***dblSrc***)** 分配**double**数字值赋给`_variant_t`对象。

- **operator=(**  *cySrc*  **)** Assigns a `CY` object to a `_variant_t` object.

- **运算符 = (***bstrSrc***)** 分配`BSTR`对象传递给`_variant_t`对象。

- **运算符 = (***wstrSrc***)** 分配给一个 Unicode 字符串`_variant_t`对象。

- **运算符 = (**`strSrc`**)** 分配到一个多字节字符串`_variant_t`对象。

- **运算符 = (** `bSrc` **)** 分配**bool**值设为`_variant_t`对象。

- **运算符 = (***pDispSrc***)** 分配`VT_DISPATCH`对象传递给`_variant_t`对象。

- **运算符 = (***pIUnknownSrc***)** 分配`VT_UNKNOWN`对象传递给`_variant_t`对象。

- **运算符 = (***decSrc***)** 分配`DECIMAL`值设为`_variant_t`对象。

- **运算符 = (** `bSrc` **)** 分配`BYTE`值设为`_variant_t`对象。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_variant_t 类](../cpp/variant-t-class.md)