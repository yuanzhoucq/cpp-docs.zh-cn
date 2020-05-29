---
title: _com_error::HelpContext
ms.date: 11/04/2016
f1_keywords:
- _com_error::HelpContext
helpviewer_keywords:
- HelpContext method [C++]
ms.assetid: 160d6443-9b68-4cf5-a540-50da951a5b2b
ms.openlocfilehash: b3c79bb069ef504680e83359d6ec90c803f16d9d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180584"
---
# <a name="_com_errorhelpcontext"></a>_com_error::HelpContext

**Microsoft 专用**

调用 `IErrorInfo::GetHelpContext` 函数。

## <a name="syntax"></a>语法

```
DWORD HelpContext( ) const throw( );
```

## <a name="return-value"></a>返回值

返回在 `_com_error` 对象内记录的 `IErrorInfo` 对象的 `IErrorInfo::GetHelpContext` 结果。 如果未记录 `IErrorInfo` 对象，则返回零。

## <a name="remarks"></a>备注

调用 `IErrorInfo::GetHelpContext` 方法时，将忽略任何错误。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[_com_error 类](../cpp/com-error-class.md)
