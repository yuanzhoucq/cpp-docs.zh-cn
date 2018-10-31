---
title: _bstr_t::operator =
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::operator=
helpviewer_keywords:
- operator = [C++], bstr
- operator= [C++], bstr
ms.assetid: fb31bb1b-ce29-4388-b5fd-8dac830cf18a
ms.openlocfilehash: 97f0100d8a34253f3a1375d34b887d3d31a77f43
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432573"
---
# <a name="bstrtoperator-"></a>_bstr_t::operator =

**Microsoft 专用**

将新值赋给现有 `_bstr_t` 对象。

## <a name="syntax"></a>语法

```
_bstr_t& operator=(const _bstr_t& s1) throw ( );
_bstr_t& operator=(const char* s2);
_bstr_t& operator=(const wchar_t* s3);
_bstr_t& operator=(const _variant_t& var);
```

#### <a name="parameters"></a>参数

*s1*<br/>
将分配给现有 `_bstr_t` 对象的 `_bstr_t` 对象。

*s2*<br/>
将分配给现有 `_bstr_t` 对象的多字节字符串。

*s3*<br/>
将分配给现有 `_bstr_t` 对象的 Unicode 字符串。

*var*<br/>
将分配给现有 `_variant_t` 对象的 `_bstr_t` 对象。

**结束 Microsoft 专用**

## <a name="example"></a>示例

请参阅[_bstr_t:: assign](../cpp/bstr-t-assign.md)有关的使用示例**运算符 =**。

## <a name="see-also"></a>请参阅

[_bstr_t 类](../cpp/bstr-t-class.md)