---
title: _com_error::HelpContext |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::HelpContext
dev_langs:
- C++
helpviewer_keywords:
- HelpContext method [C++]
ms.assetid: 160d6443-9b68-4cf5-a540-50da951a5b2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c2a1810410194f1261da907199a3b6665e5be30
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074365"
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