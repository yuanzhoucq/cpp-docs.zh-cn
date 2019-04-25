---
title: _com_error::_com_error
ms.date: 11/04/2016
f1_keywords:
- _com_error::_com_error
helpviewer_keywords:
- _com_error method [C++]
ms.assetid: 0a69e46c-caab-49ef-b091-eee401253ce6
ms.openlocfilehash: 8856289605cce430fdab36d6e3e8b743190e02ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155119"
---
# <a name="comerrorcomerror"></a>_com_error::_com_error

**Microsoft 专用**

构造 **_com_error**对象。

## <a name="syntax"></a>语法

```
_com_error(
   HRESULT hr,
   IErrorInfo* perrinfo = NULL,
   bool fAddRef=false) throw( );

_com_error( const _com_error& that ) throw( );
```

#### <a name="parameters"></a>参数

*hr*<br/>
HRESULT 的信息。

*perrinfo*<br/>
`IErrorInfo` 对象。

*fAddRef*<br/>
默认值会导致构造函数非 null 值调用 AddRef`IErrorInfo`接口。 这提供了正确的引用计数的常见的情况下，其中在接口的所有权传递给 **_com_error**对象，例如：

```cpp
throw _com_error(hr, perrinfo);
```

如果不希望您的代码以将所有权转移给 **_com_error**对象，并`AddRef`偏移需要`Release`中 **_com_error**析构函数中，构造对象作为如下所示：

```cpp
_com_error err(hr, perrinfo, true);
```

*that*<br/>
将现有 **_com_error**对象。

## <a name="remarks"></a>备注

第一个构造函数创建新的对象在给定的 HRESULT 和可选`IErrorInfo`对象。 第二个创建的现有副本 **_com_error**对象。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_com_error 类](../cpp/com-error-class.md)