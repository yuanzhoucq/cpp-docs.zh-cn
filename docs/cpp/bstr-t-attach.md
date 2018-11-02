---
title: _bstr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::Attach
helpviewer_keywords:
- Attach method [C++]
ms.assetid: 8cad867e-40fc-435b-841f-0d412c2f58d3
ms.openlocfilehash: 8601ebbea6a9ab837c07518b018e83e8c0df226d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604433"
---
# <a name="bstrtattach"></a>_bstr_t::Attach

**Microsoft 专用**

将 `_bstr_t` 包装器链接到 `BSTR`。

## <a name="syntax"></a>语法

```
void Attach(
   BSTR s
);
```

#### <a name="parameters"></a>参数

*s*<br/>
要与之关联或分配到的 `BSTR`，即 `_bstr_t` 变量。

## <a name="remarks"></a>备注

如果 `_bstr_t` 以前被附加到了另一个 `BSTR`，并且没有其他 `_bstr_t` 变量使用 `BSTR`，`_bstr_t` 将清理 `BSTR` 资源。

## <a name="example"></a>示例

请参阅[_bstr_t:: assign](../cpp/bstr-t-assign.md)示例使用**附加**。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_bstr_t 类](../cpp/bstr-t-class.md)