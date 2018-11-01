---
title: _com_error::operator =
ms.date: 11/04/2016
f1_keywords:
- _com_error::operator=
helpviewer_keywords:
- operator= _com_error objects
- = operator [C++], with specific Visual C++ objects
- operator = _com_error objects
ms.assetid: b9cc4094-d055-450c-b45a-0a95317488f8
ms.openlocfilehash: 68eb486ec109d98890ebf3adc0c086368380142b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449590"
---
# <a name="comerroroperator-"></a>_com_error::operator =

**Microsoft 专用**

将现有 `_com_error` 对象赋给另一个对象。

## <a name="syntax"></a>语法

```
_com_error& operator = (
   const _com_error& that
) throw ( );
```

#### <a name="parameters"></a>参数

*的*<br/>
一个 `_com_error` 对象。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_com_error 类](../cpp/com-error-class.md)