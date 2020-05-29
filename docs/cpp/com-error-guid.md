---
title: _com_error::GUID
ms.date: 11/04/2016
f1_keywords:
- _com_error::GUID
helpviewer_keywords:
- GUID method [C++]
ms.assetid: e84c2c23-d02e-48f8-b776-9bd6937296d2
ms.openlocfilehash: d5b05cd4e26f89d42ea23b605f5e6560795a0cfa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180636"
---
# <a name="_com_errorguid"></a>_com_error::GUID

**Microsoft 专用**

调用 `IErrorInfo::GetGUID` 函数。

## <a name="syntax"></a>语法

```
GUID GUID( ) const throw( );
```

## <a name="return-value"></a>返回值

返回在 `_com_error` 对象内记录的 `IErrorInfo` 对象的 `IErrorInfo::GetGUID` 结果。 如果未记录 `IErrorInfo` 对象，它将返回 `GUID_NULL`。

## <a name="remarks"></a>备注

调用 `IErrorInfo::GetGUID` 方法时，将忽略任何错误。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[_com_error 类](../cpp/com-error-class.md)
