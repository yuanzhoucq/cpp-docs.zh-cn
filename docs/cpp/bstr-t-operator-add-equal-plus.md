---
title: _bstr_t::operator +=, +
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::operator+
- _bstr_t::operator+=
helpviewer_keywords:
- += operator [C++], appending strings
- + operator [C++], _bstr_t objects
ms.assetid: d28316ce-c2c8-4a38-bdb3-44fa4e582c44
ms.openlocfilehash: b9eddca85d66f4978e1b33299ca655cd880cf45e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181143"
---
# <a name="_bstr_toperator--"></a>_bstr_t::operator +=, +

**Microsoft 专用**

将字符追加到 `_bstr_t` 对象的结尾或串联两个字符串。

## <a name="syntax"></a>语法

```
_bstr_t& operator+=( const _bstr_t& s1 );
_bstr_t operator+( const _bstr_t& s1 );
friend _bstr_t operator+( const char* s2, const _bstr_t& s1);
friend _bstr_t operator+( const wchar_t* s3, const _bstr_t& s1);
```

#### <a name="parameters"></a>parameters

s1<br/>
`_bstr_t` 对象。

s2<br/>
多字节字符串。

*s3*<br/>
一个 Unicode 字符串。

## <a name="remarks"></a>备注

以下运算符将执行字符串串联：

- **operator + = （** *s1* **）** 将*s1*的封装 `BSTR` 中的字符追加到该对象的封装 `BSTR`的末尾。

- **operator + （** *s1* **）** 返回通过将此对象的 `BSTR` 与*s1*进行连接而形成的新 `_bstr_t`。

- **operator + （**  *s2*  **&#124;**  *s1*  **）** 返回一个新的 `_bstr_t`，该通过将多字节字符串*s2*连接起来（转换为 Unicode），并将 `BSTR` 封装在*s1*中形成。

- **operator + （** *s3* **，** *s1* **）** 返回一个新的 `_bstr_t`，通过将 Unicode 字符串*s3*与*s1*中封装的 `BSTR` 连接起来形成。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[_bstr_t 类](../cpp/bstr-t-class.md)
