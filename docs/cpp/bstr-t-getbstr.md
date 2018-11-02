---
title: _bstr_t::GetBSTR
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetBSTR
helpviewer_keywords:
- GetBSTR method [C++]
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
ms.openlocfilehash: cea3404e0732cb0e16b3fa9199ce95e3dfcc23f5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618044"
---
# <a name="bstrtgetbstr"></a>_bstr_t::GetBSTR

**Microsoft 专用**

指向 `BSTR` 包装的 `_bstr_t` 的开头。

## <a name="syntax"></a>语法

```
BSTR& GetBSTR( );
```

## <a name="return-value"></a>返回值

`BSTR` 包装的 `_bstr_t` 的开头。

## <a name="remarks"></a>备注

**GetBSTR**影响所有`_bstr_t`对象的共享`BSTR`。 多个`_bstr_t`可以共享`BSTR`通过使用复制构造函数和**运算符 =**。

## <a name="example"></a>示例

请参阅[_bstr_t:: assign](../cpp/bstr-t-assign.md)示例使用**GetBSTR**。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_bstr_t 类](../cpp/bstr-t-class.md)