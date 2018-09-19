---
title: _bstr_t::Attach |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::Attach
dev_langs:
- C++
helpviewer_keywords:
- Attach method [C++]
ms.assetid: 8cad867e-40fc-435b-841f-0d412c2f58d3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1eddbc7a01be66430759bb84c3ce6d840f37d098
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111207"
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