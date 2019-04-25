---
title: _com_error::Description
ms.date: 11/04/2016
f1_keywords:
- _com_error::Description
helpviewer_keywords:
- Description method [C++]
ms.assetid: 88191e24-4ee8-44a6-8c4c-3758e22e0548
ms.openlocfilehash: a517c40e9adfbda2d790ce41a48ccf8658bcd3e0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155106"
---
# <a name="comerrordescription"></a>_com_error::Description

**Microsoft 专用**

调用`IErrorInfo::GetDescription`函数。

## <a name="syntax"></a>语法

```
_bstr_t Description( ) const;
```

## <a name="return-value"></a>返回值

返回的结果`IErrorInfo::GetDescription`有关`IErrorInfo`对象中记录`_com_error`对象。 生成的 `BSTR` 封装在 `_bstr_t` 对象中。 如果没有`IErrorInfo`是记录，返回一个空`_bstr_t`。

## <a name="remarks"></a>备注

调用`IErrorInfo::GetDescription`函数并检索`IErrorInfo`记录`_com_error`对象。 调用时的任何错误`IErrorInfo::GetDescription`方法将被忽略。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_com_error 类](../cpp/com-error-class.md)