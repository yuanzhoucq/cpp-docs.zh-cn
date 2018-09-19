---
title: _com_error::Error |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::Error
- Error
dev_langs:
- C++
helpviewer_keywords:
- Error method [C++]
ms.assetid: b53a15fd-198e-4276-afcd-13439c4807f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d56fcf7faaee9d3b0e02964163aa62372a30a78
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109285"
---
# <a name="comerrorerror"></a>_com_error::Error

**Microsoft 专用**

检索传递给构造函数的 HRESULT。

## <a name="syntax"></a>语法

```
HRESULT Error( ) const throw( );
```

## <a name="return-value"></a>返回值

原始 HRESULT 项传递到构造函数。

## <a name="remarks"></a>备注

检索中的封装的 HRESULT 项`_com_error`对象。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_com_error 类](../cpp/com-error-class.md)