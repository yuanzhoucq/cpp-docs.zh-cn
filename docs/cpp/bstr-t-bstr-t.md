---
title: _bstr_t::_bstr_t
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::_bstr_t
helpviewer_keywords:
- BSTR object
- _bstr_t method [C++]
- _bstr_t class
ms.assetid: 116d994e-5a72-4351-afbe-866c80b4c165
ms.openlocfilehash: 3384da733586c828496a8728a0f5855f92eeec35
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190464"
---
# <a name="_bstr_t_bstr_t"></a>_bstr_t::_bstr_t

**Microsoft 专用**

构造 `_bstr_t` 对象。

## <a name="syntax"></a>语法

```
_bstr_t( ) throw( );
_bstr_t(
   const _bstr_t& s1
) throw( );
_bstr_t(
   const char* s2
);
_bstr_t(
   const wchar_t* s3
);
_bstr_t(
   const _variant_t& var
);
_bstr_t(
   BSTR bstr,
   bool fCopy
);
```

#### <a name="parameters"></a>parameters

s1<br/>
要复制的 `_bstr_t` 对象。

s2<br/>
多字节字符串。

*s3*<br/>
Unicode 字符串

*var*<br/>
一个[_variant_t](../cpp/variant-t-class.md)对象。

*bstr*<br/>
一个现有的 `BSTR` 对象。

*fCopy*<br/>
如果为 FALSE，则会将*bstr*参数附加到新的对象，而不会通过调用 `SysAllocString`进行复制。

## <a name="remarks"></a>备注

下表描述 `_bstr_t` 构造函数。

|构造函数|说明|
|-----------------|-----------------|
|`_bstr_t( )`|构造一个默认 `_bstr_t` 对象，该对象封装 null `BSTR` 对象。|
|`_bstr_t( _bstr_t&`  `s1`  `)`|构造一个 `_bstr_t` 对象作为另一个对象的副本。<br /><br /> 这是一个*浅表*复制，它递增封装 `BSTR` 对象的引用计数，而不是创建新对象。|
|`_bstr_t( char*`  `s2`  `)`|通过调用 `_bstr_t` 来创建一个新的 `SysAllocString` 对象并封装该对象，从而构造一个 `BSTR` 对象。<br /><br /> 此构造函数首先执行多字节到 Unicode 的转换。|
|`_bstr_t( wchar_t*`  `s3`  `)`|通过调用 `_bstr_t` 来创建一个新的 `SysAllocString` 对象并封装该对象，从而构造一个 `BSTR` 对象。|
|`_bstr_t( _variant_t&`  `var`  `)`|通过先从封装的 VARIANT 对象检查 `_bstr_t` 对象来从 `_variant_t` 对象构造一个 `BSTR` 对象。|
|`_bstr_t( BSTR``bstr` `, bool``fCopy``)`|从现有 `_bstr_t` 构造一个 `BSTR` 对象（与 `wchar_t*` 字符串相对）。 如果*fCopy*为 false，则提供的 `BSTR` 会附加到新的对象，而不会生成 `SysAllocString`的新副本。<br /><br /> 此构造函数由类型库标头中的包装器函数用于封装接口方法所返回的 `BSTR` 并获取其所有权。|

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[_bstr_t 类](../cpp/bstr-t-class.md)<br/>
[_variant_t 类](../cpp/variant-t-class.md)
