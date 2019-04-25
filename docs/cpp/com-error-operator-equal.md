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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154989"
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

*that*<br/>
一个 `_com_error` 对象。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_com_error 类](../cpp/com-error-class.md)