---
title: _bstr_t::copy
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::copy
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
ms.openlocfilehash: 1fe8cfb5b644b3c7c34cf3325a91ebdf23a04946
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190321"
---
# <a name="_bstr_tcopy"></a>_bstr_t::copy

**Microsoft 专用**

构造封装的 `BSTR` 的副本。

## <a name="syntax"></a>语法

```
BSTR copy( bool fCopy = true ) const;
```

#### <a name="parameters"></a>parameters

*fCopy*<br/>
如果为 TRUE，则**copy**返回包含 `BSTR`的副本，否则**copy**返回实际的 BSTR。

## <a name="remarks"></a>备注

返回封装的 `BSTR` 对象的新分配的副本。

## <a name="example"></a>示例

```cpp
STDMETHODIMP CAlertMsg::get_ConnectionStr(BSTR *pVal){ //  m_bsConStr is _bstr_t
   *pVal = m_bsConStr.copy();
}
```

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[_bstr_t 类](../cpp/bstr-t-class.md)
