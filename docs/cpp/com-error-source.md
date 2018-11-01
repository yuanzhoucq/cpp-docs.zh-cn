---
title: _com_error::Source
ms.date: 11/04/2016
f1_keywords:
- _com_error::Source
helpviewer_keywords:
- Source method [C++]
ms.assetid: 55353741-fabc-4b0c-9787-b5a69bb189f2
ms.openlocfilehash: 682070877f269967405677d027b20707c8366f61
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644426"
---
# <a name="comerrorsource"></a>_com_error::Source

**Microsoft 专用**

调用`IErrorInfo::GetSource`函数。

## <a name="syntax"></a>语法

```
_bstr_t Source() const;
```

## <a name="return-value"></a>返回值

返回的结果`IErrorInfo::GetSource`有关`IErrorInfo`对象中记录`_com_error`对象。 生成的 `BSTR` 封装在 `_bstr_t` 对象中。 如果没有`IErrorInfo`是记录，返回一个空`_bstr_t`。

## <a name="remarks"></a>备注

调用时的任何错误`IErrorInfo::GetSource`方法将被忽略。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_com_error 类](../cpp/com-error-class.md)