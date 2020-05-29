---
title: _com_error::HelpFile
ms.date: 11/04/2016
f1_keywords:
- _com_error::HelpFile
helpviewer_keywords:
- HelpFile method [C++]
ms.assetid: d2d3a0a1-6b62-4d52-a818-3cfae545a4af
ms.openlocfilehash: 775adfa7d5dd5aca098edcd793c2164d65fe7efa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190217"
---
# <a name="_com_errorhelpfile"></a>_com_error::HelpFile

**Microsoft 专用**

调用 `IErrorInfo::GetHelpFile` 函数。

## <a name="syntax"></a>语法

```
_bstr_t HelpFile() const;
```

## <a name="return-value"></a>返回值

返回在 `_com_error` 对象内记录的 `IErrorInfo` 对象的 `IErrorInfo::GetHelpFile` 结果。 生成的 BSTR 封装在 `_bstr_t` 对象中。 如果未记录任何 `IErrorInfo`，它将返回一个空 `_bstr_t`。

## <a name="remarks"></a>备注

调用 `IErrorInfo::GetHelpFile` 方法时，将忽略任何错误。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[_com_error 类](../cpp/com-error-class.md)
