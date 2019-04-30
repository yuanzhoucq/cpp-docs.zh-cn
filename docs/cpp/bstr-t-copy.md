---
title: _bstr_t::copy
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::copy
helpviewer_keywords:
- Copy method [C++]
- BSTR object [C++], copy
ms.assetid: 00ba7311-e82e-4a79-8106-5329fa2f869a
ms.openlocfilehash: 13ddf57e0bdbdbcc0c5b487e879e14b000de3ad0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393930"
---
# <a name="bstrtcopy"></a>_bstr_t::copy

**Microsoft 专用**

构造封装的 `BSTR` 的副本。

## <a name="syntax"></a>语法

```
BSTR copy( bool fCopy = true ) const;
```

#### <a name="parameters"></a>参数

*fCopy*<br/>
如果为 TRUE，**副本**返回所包含的一个副本`BSTR`; 否则为**副本**返回实际的 BSTR。

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