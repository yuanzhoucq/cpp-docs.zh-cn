---
title: _com_error::ErrorInfo |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::ErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- ErrorInfo method [C++]
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1fc2906827e6a465106a3dbdcb8b63c7b53a39ee
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039343"
---
# <a name="comerrorerrorinfo"></a>_com_error::ErrorInfo

**Microsoft 专用**

检索`IErrorInfo`对象传递给构造函数。

## <a name="syntax"></a>语法

```
IErrorInfo * ErrorInfo( ) const throw( );
```

## <a name="return-value"></a>返回值

已传入构造函数的原始 `IErrorInfo` 项。

## <a name="remarks"></a>备注

检索封装`IErrorInfo`中的项`_com_error`对象，或者如果没有，则为 NULL`IErrorInfo`项未记录。 调用方必须调用`Release`对返回的对象完成后使用它。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_com_error 类](../cpp/com-error-class.md)