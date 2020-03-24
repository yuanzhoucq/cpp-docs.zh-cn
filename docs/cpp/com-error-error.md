---
title: _com_error::Error
ms.date: 11/04/2016
f1_keywords:
- _com_error::Error
- Error
helpviewer_keywords:
- Error method [C++]
ms.assetid: b53a15fd-198e-4276-afcd-13439c4807f7
ms.openlocfilehash: 8e2c52d10b15822703329dcea18944773f5784ea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180753"
---
# <a name="_com_errorerror"></a>_com_error::Error

**Microsoft 专用**

检索传递给构造函数的 HRESULT。

## <a name="syntax"></a>语法

```
HRESULT Error( ) const throw( );
```

## <a name="return-value"></a>返回值

传入构造函数的原始 HRESULT 项。

## <a name="remarks"></a>备注

检索 `_com_error` 对象中封装的 HRESULT 项。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[_com_error 类](../cpp/com-error-class.md)
