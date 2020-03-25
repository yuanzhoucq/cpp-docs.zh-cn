---
title: _bstr_t::GetBSTR
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetBSTR
helpviewer_keywords:
- GetBSTR method [C++]
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
ms.openlocfilehash: da438c65256d9a7e5bf5b02e108fee1385171d2d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181208"
---
# <a name="_bstr_tgetbstr"></a>_bstr_t::GetBSTR

**Microsoft 专用**

指向 `BSTR` 包装的 `_bstr_t` 的开头。

## <a name="syntax"></a>语法

```
BSTR& GetBSTR( );
```

## <a name="return-value"></a>返回值

`BSTR` 包装的 `_bstr_t` 的开头。

## <a name="remarks"></a>备注

**GetBSTR**影响所有共享 `BSTR`的 `_bstr_t` 对象。 多个 `_bstr_t` 可以通过使用复制构造函数和**运算符 =** 来共享 `BSTR`。

## <a name="example"></a>示例

有关使用**GetBSTR**的示例，请参阅[_Bstr_t：： Assign](../cpp/bstr-t-assign.md) 。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[_bstr_t 类](../cpp/bstr-t-class.md)
