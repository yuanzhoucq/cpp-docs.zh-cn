---
title: _com_error::HelpContext
ms.date: 11/04/2016
f1_keywords:
- _com_error::HelpContext
helpviewer_keywords:
- HelpContext method [C++]
ms.assetid: 160d6443-9b68-4cf5-a540-50da951a5b2b
ms.openlocfilehash: a421a7fd7fa0817c74dac66946e28928b2ad82dc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155080"
---
# <a name="comerrorhelpcontext"></a>_com_error::HelpContext

**Microsoft 专用**

调用`IErrorInfo::GetHelpContext`函数。

## <a name="syntax"></a>语法

```
DWORD HelpContext( ) const throw( );
```

## <a name="return-value"></a>返回值

返回的结果`IErrorInfo::GetHelpContext`有关`IErrorInfo`对象中记录`_com_error`对象。 如果没有`IErrorInfo`记录对象，它将返回零。

## <a name="remarks"></a>备注

调用时的任何错误`IErrorInfo::GetHelpContext`方法将被忽略。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_com_error 类](../cpp/com-error-class.md)