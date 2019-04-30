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
ms.openlocfilehash: 0a2c374fc160a0575e0a17cc85ab51c65fa9392a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390823"
---
# <a name="bstrtoperator--"></a>_bstr_t::operator +=, +

**Microsoft 专用**

将字符追加到 `_bstr_t` 对象的结尾或串联两个字符串。

## <a name="syntax"></a>语法

```
_bstr_t& operator+=( const _bstr_t& s1 );
_bstr_t operator+( const _bstr_t& s1 );
friend _bstr_t operator+( const char* s2, const _bstr_t& s1);
friend _bstr_t operator+( const wchar_t* s3, const _bstr_t& s1);
```

#### <a name="parameters"></a>参数

*s1*<br/>
一个 `_bstr_t` 对象。

*s2*<br/>
多字节字符串。

*s3*<br/>
一个 Unicode 字符串。

## <a name="remarks"></a>备注

以下运算符将执行字符串串联：

- **operator + = (***s1***)** 中封装的字符追加`BSTR`的*s1*到此对象封装末尾`BSTR`.

- **operator + (***s1***)** 返回新`_bstr_t`此对象的连接在一起构成`BSTR`与*s1*。

- **operator + (***s2***&#124;***s1***)** 返回一个新`_bstr_t`通过串联构成多字节字符串*s2*，已转换为 Unicode，与`BSTR`封装在*s1*。

- **operator + (***s3* **，***s1***)** 返回一个新`_bstr_t`通过将 Unicode 字符串构成*s3*与`BSTR`封装在*s1*。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_bstr_t 类](../cpp/bstr-t-class.md)