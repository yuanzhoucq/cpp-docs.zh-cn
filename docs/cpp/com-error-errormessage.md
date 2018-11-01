---
title: _com_error::ErrorMessage
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorMessage
helpviewer_keywords:
- ErrorMessage method [C++]
ms.assetid: e47335b6-01af-4975-a841-121597479eb7
ms.openlocfilehash: b1c1b5a79cdf5ee2a4a17d969d23ce0d0d85ab54
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50504489"
---
# <a name="comerrorerrormessage"></a>_com_error::ErrorMessage

**Microsoft 专用**

HRESULT 存储中检索的字符串消息`_com_error`对象。

## <a name="syntax"></a>语法

```
const TCHAR * ErrorMessage( ) const throw( );
```

## <a name="return-value"></a>返回值

中记录相应的 HRESULT 返回的字符串消息`_com_error`对象。 如果 HRESULT 为映射的 16 位[wCode](../cpp/com-error-wcode.md)，然后一条常规消息"`IDispatch error #<wCode>`"返回。 如果未找到消息，则返回一般消息“`Unknown error #<hresult>`”。 返回的字符串是 Unicode 或多字节字符串，具体取决于 _UNICODE 宏的状态。

## <a name="remarks"></a>备注

HRESULT 记录中检索相应的系统消息文本`_com_error`对象。 系统消息文本通过调用 Win32 [FormatMessage](/windows/desktop/api/winbase/nf-winbase-formatmessage)函数。 返回的字符串由 `FormatMessage` API 分配，并在销毁 `_com_error` 对象后释放。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_com_error 类](../cpp/com-error-class.md)