---
title: _com_error::ErrorMessage
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorMessage
helpviewer_keywords:
- ErrorMessage method [C++]
ms.assetid: e47335b6-01af-4975-a841-121597479eb7
ms.openlocfilehash: 44fc9755cd69050ea82145636f01614258943794
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500579"
---
# <a name="_com_errorerrormessage"></a>_com_error::ErrorMessage

**Microsoft 专用**

检索`_com_error`对象中存储的 HRESULT 的字符串消息。

## <a name="syntax"></a>语法

```
const TCHAR * ErrorMessage( ) const throw( );
```

## <a name="return-value"></a>返回值

返回在`_com_error`对象中记录的 HRESULT 的字符串消息。 如果 HRESULT 是映射的16位[wCode](../cpp/com-error-wcode.md), 则返回一般消息 "`IDispatch error #<wCode>`"。 如果未找到消息，则返回一般消息“`Unknown error #<hresult>`”。 返回的字符串是 Unicode 或多字节字符串, 具体取决于 _UNICODE 宏的状态。

## <a name="remarks"></a>备注

检索在`_com_error`对象中记录的 HRESULT 的适当系统消息文本。 系统消息文本是通过调用 Win32 [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage)函数获取的。 返回的字符串由 `FormatMessage` API 分配，并在销毁 `_com_error` 对象后释放。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_com_error 类](../cpp/com-error-class.md)