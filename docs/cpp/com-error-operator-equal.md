---
title: _com_error::operator =
ms.date: 11/04/2016
f1_keywords:
- _com_error::operator=
helpviewer_keywords:
- _com_error [C++]
ms.assetid: b9cc4094-d055-450c-b45a-0a95317488f8
ms.openlocfilehash: 1c68d10c8f82f5d5ed7f6286ba15437941c0ac6b
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222492"
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