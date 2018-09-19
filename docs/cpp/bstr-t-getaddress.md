---
title: _bstr_t::GetAddress |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::GetAddress
dev_langs:
- C++
helpviewer_keywords:
- GetAddress method [C++]
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9b3aa001270a3dc608fabf73fce28ce51eb9295e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031296"
---
# <a name="bstrtgetaddress"></a>_bstr_t::GetAddress

**Microsoft 专用**

释放所有现有字符串并返回一个新分配的字符串的地址。

## <a name="syntax"></a>语法

```
BSTR* GetAddress( );
```

## <a name="return-value"></a>返回值

指向由 `BSTR` 包装的 `_bstr_t` 的指针。

## <a name="remarks"></a>备注

**GetAddress**影响所有`_bstr_t`对象的共享`BSTR`。 多个`_bstr_t`可以共享`BSTR`通过使用复制构造函数和**运算符 =**。

## <a name="example"></a>示例

请参阅[_bstr_t:: assign](../cpp/bstr-t-assign.md)示例使用**GetAddress**。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_bstr_t 类](../cpp/bstr-t-class.md)