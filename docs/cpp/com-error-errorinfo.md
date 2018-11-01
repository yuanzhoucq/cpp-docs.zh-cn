---
title: _com_error::ErrorInfo
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorInfo
helpviewer_keywords:
- ErrorInfo method [C++]
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
ms.openlocfilehash: 59ada8a7e098e57cca5641a439365851bbae2485
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558994"
---
# <a name="comerrorerrorinfo"></a>_com_error::ErrorInfo

**Microsoft 专用**

检索`IErrorInfo`对象传递给构造函数。

## <a name="syntax"></a>语法

```
IErrorInfo * ErrorInfo( ) const throw( );
```

## <a name="return-value"></a>返回值

已传入构造函数的原始 `IErrorInfo` 项。

## <a name="remarks"></a>备注

检索封装`IErrorInfo`中的项`_com_error`对象，或者如果没有，则为 NULL`IErrorInfo`项未记录。 调用方必须调用`Release`对返回的对象完成后使用它。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_com_error 类](../cpp/com-error-class.md)