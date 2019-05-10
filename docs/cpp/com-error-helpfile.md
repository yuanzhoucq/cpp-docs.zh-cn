---
title: _com_error::HelpFile
ms.date: 11/04/2016
f1_keywords:
- _com_error::HelpFile
helpviewer_keywords:
- HelpFile method [C++]
ms.assetid: d2d3a0a1-6b62-4d52-a818-3cfae545a4af
ms.openlocfilehash: 826ac53f001355127f16b7ad2a7583a0f8800de7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155028"
---
# <a name="comerrorhelpfile"></a>_com_error::HelpFile

**Microsoft 专用**

调用`IErrorInfo::GetHelpFile`函数。

## <a name="syntax"></a>语法

```
_bstr_t HelpFile() const;
```

## <a name="return-value"></a>返回值

返回的结果`IErrorInfo::GetHelpFile`有关`IErrorInfo`对象中记录`_com_error`对象。 生成的 BSTR 封装在 `_bstr_t` 对象中。 如果没有`IErrorInfo`是记录，返回一个空`_bstr_t`。

## <a name="remarks"></a>备注

调用时的任何错误`IErrorInfo::GetHelpFile`方法将被忽略。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_com_error 类](../cpp/com-error-class.md)