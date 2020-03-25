---
title: _com_error::ErrorInfo
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorInfo
helpviewer_keywords:
- ErrorInfo method [C++]
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
ms.openlocfilehash: cedb9ccadc63166c43d980333d93a195254700d8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180701"
---
# <a name="_com_errorerrorinfo"></a>_com_error::ErrorInfo

**Microsoft 专用**

检索传递给构造函数的 `IErrorInfo` 对象。

## <a name="syntax"></a>语法

```
IErrorInfo * ErrorInfo( ) const throw( );
```

## <a name="return-value"></a>返回值

已传入构造函数的原始 `IErrorInfo` 项。

## <a name="remarks"></a>备注

检索 `_com_error` 对象中封装的 `IErrorInfo` 项; 如果不记录 `IErrorInfo` 项，则为 NULL。 使用完后，调用方必须对返回的对象调用 `Release`。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[_com_error 类](../cpp/com-error-class.md)
