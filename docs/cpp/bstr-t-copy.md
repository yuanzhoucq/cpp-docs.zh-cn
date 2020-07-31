---
title: _bstr_t::copy
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::copy
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
ms.openlocfilehash: b6029e98e83b171d9ab9f8f3f0282fa3f46ca167
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227590"
---
# <a name="_bstr_tcopy"></a>_bstr_t::copy

**Microsoft 专用**

构造封装的 `BSTR` 的副本。

## <a name="syntax"></a>语法

```
BSTR copy( bool fCopy = true ) const;
```

#### <a name="parameters"></a>参数

*fCopy*<br/>
如果 **`true`** 为，则**copy**返回包含的副本 `BSTR` ，否则**copy**返回实际的 BSTR。

## <a name="remarks"></a>备注

返回封装的 `BSTR` 对象的新分配的副本。

## <a name="example"></a>示例

```cpp
STDMETHODIMP CAlertMsg::get_ConnectionStr(BSTR *pVal){ //  m_bsConStr is _bstr_t
   *pVal = m_bsConStr.copy();
}
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_bstr_t 类](../cpp/bstr-t-class.md)
