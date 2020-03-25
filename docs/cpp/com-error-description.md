---
title: _com_error::Description
ms.date: 11/04/2016
f1_keywords:
- _com_error::Description
helpviewer_keywords:
- Description method [C++]
ms.assetid: 88191e24-4ee8-44a6-8c4c-3758e22e0548
ms.openlocfilehash: de2275f096fe2fde96e64cbc3034602a1fde5e88
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180766"
---
# <a name="_com_errordescription"></a>_com_error::Description

**Microsoft 专用**

调用 `IErrorInfo::GetDescription` 函数。

## <a name="syntax"></a>语法

```
_bstr_t Description( ) const;
```

## <a name="return-value"></a>返回值

返回在 `_com_error` 对象内记录的 `IErrorInfo` 对象的 `IErrorInfo::GetDescription` 结果。 生成的 `BSTR` 封装在 `_bstr_t` 对象中。 如果未记录任何 `IErrorInfo`，它将返回一个空 `_bstr_t`。

## <a name="remarks"></a>备注

调用 `IErrorInfo::GetDescription` 函数并检索 `_com_error` 对象内记录的 `IErrorInfo`。 调用 `IErrorInfo::GetDescription` 方法时，将忽略任何错误。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[_com_error 类](../cpp/com-error-class.md)
