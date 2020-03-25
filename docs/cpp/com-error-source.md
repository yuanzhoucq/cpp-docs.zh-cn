---
title: _com_error::Source
ms.date: 11/04/2016
f1_keywords:
- _com_error::Source
helpviewer_keywords:
- Source method [C++]
ms.assetid: 55353741-fabc-4b0c-9787-b5a69bb189f2
ms.openlocfilehash: 43dd21297ddd54863d535402dddd59243d589eec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180519"
---
# <a name="_com_errorsource"></a>_com_error::Source

**Microsoft 专用**

调用 `IErrorInfo::GetSource` 函数。

## <a name="syntax"></a>语法

```
_bstr_t Source() const;
```

## <a name="return-value"></a>返回值

返回在 `_com_error` 对象内记录的 `IErrorInfo` 对象的 `IErrorInfo::GetSource` 结果。 生成的 `BSTR` 封装在 `_bstr_t` 对象中。 如果未记录任何 `IErrorInfo`，它将返回一个空 `_bstr_t`。

## <a name="remarks"></a>备注

调用 `IErrorInfo::GetSource` 方法时，将忽略任何错误。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[_com_error 类](../cpp/com-error-class.md)
