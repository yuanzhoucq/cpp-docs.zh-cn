---
title: _com_error::GUID
ms.date: 11/04/2016
f1_keywords:
- _com_error::GUID
helpviewer_keywords:
- GUID method [C++]
ms.assetid: e84c2c23-d02e-48f8-b776-9bd6937296d2
ms.openlocfilehash: 905b67577a65b81be0b4d18c7513652dd8c5f055
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155054"
---
# <a name="comerrorguid"></a>_com_error::GUID

**Microsoft 专用**

调用`IErrorInfo::GetGUID`函数。

## <a name="syntax"></a>语法

```
GUID GUID( ) const throw( );
```

## <a name="return-value"></a>返回值

返回的结果`IErrorInfo::GetGUID`有关`IErrorInfo`对象中记录`_com_error`对象。 如果没有`IErrorInfo`记录对象时，它将返回`GUID_NULL`。

## <a name="remarks"></a>备注

调用时的任何错误`IErrorInfo::GetGUID`方法将被忽略。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_com_error 类](../cpp/com-error-class.md)