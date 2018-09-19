---
title: _com_error::Description |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::Description
dev_langs:
- C++
helpviewer_keywords:
- Description method [C++]
ms.assetid: 88191e24-4ee8-44a6-8c4c-3758e22e0548
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90208866ee08d6990d8f1b5322a38fbd2d63a651
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091774"
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