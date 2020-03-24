---
title: _com_error::_com_error
ms.date: 11/04/2016
f1_keywords:
- _com_error::_com_error
helpviewer_keywords:
- _com_error method [C++]
ms.assetid: 0a69e46c-caab-49ef-b091-eee401253ce6
ms.openlocfilehash: 4ac902f0fda90f77526ef53139ef0d523d8c22e7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180779"
---
# <a name="_com_error_com_error"></a>_com_error::_com_error

**Microsoft 专用**

构造一个 **_com_error**对象。

## <a name="syntax"></a>语法

```
_com_error(
   HRESULT hr,
   IErrorInfo* perrinfo = NULL,
   bool fAddRef=false) throw( );

_com_error( const _com_error& that ) throw( );
```

#### <a name="parameters"></a>parameters

*人事*<br/>
HRESULT 信息。

*perrinfo*<br/>
`IErrorInfo` 对象。

*fAddRef*<br/>
默认情况下，构造函数对非 null `IErrorInfo` 接口调用 AddRef。 这会在将接口所有权传递到 **_com_error**对象的常见情况下提供正确的引用计数，例如：

```cpp
throw _com_error(hr, perrinfo);
```

如果你不想让代码将所有权转移到 **_com_error**对象，而 `AddRef` 需要在 **_com_error**析构函数中偏移 `Release`，则按如下方式构造对象：

```cpp
_com_error err(hr, perrinfo, true);
```

*就*<br/>
现有的 **_com_error**对象。

## <a name="remarks"></a>备注

第一个构造函数将创建一个新的对象，给定 HRESULT 和可选的 `IErrorInfo` 对象。 第二个创建现有 **_com_error**对象的副本。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[_com_error 类](../cpp/com-error-class.md)
