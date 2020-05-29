---
title: _com_error::ErrorMessage
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorMessage
helpviewer_keywords:
- ErrorMessage method [C++]
ms.assetid: e47335b6-01af-4975-a841-121597479eb7
ms.openlocfilehash: b5e884956b5a51d3c714f1a81dc6945409f74f4b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180662"
---
# <a name="_com_errorerrormessage"></a>_com_error::ErrorMessage

**Microsoft 专用**

检索 `_com_error` 对象中存储的 HRESULT 的字符串消息。

## <a name="syntax"></a>语法

```
const TCHAR * ErrorMessage( ) const throw( );
```

## <a name="return-value"></a>返回值

返回 `_com_error` 对象中记录的 HRESULT 的字符串消息。 如果 HRESULT 是映射的16位[wCode](../cpp/com-error-wcode.md)，则返回一般消息 "`IDispatch error #<wCode>`"。 如果未找到消息，则返回一般消息“`Unknown error #<hresult>`”。 返回的字符串是 Unicode 或多字节字符串，具体取决于 _UNICODE 宏的状态。

## <a name="remarks"></a>备注

为 `_com_error` 对象中记录的 HRESULT 检索相应的系统消息文本。 系统消息文本是通过调用 Win32 [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage)函数获取的。 返回的字符串由 `FormatMessage` API 分配，并在销毁 `_com_error` 对象后释放。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[_com_error 类](../cpp/com-error-class.md)
