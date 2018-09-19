---
title: _bstr_t::length |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::length
dev_langs:
- C++
helpviewer_keywords:
- length method [C++]
- BSTR object [C++], length
ms.assetid: 4f2e2c76-8894-4ef9-833f-4c6e796d0654
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c38ff10368ff31cfd9da435e117c6619735b6274
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070491"
---
# <a name="bstrtlength"></a>_bstr_t::length

**Microsoft 专用**

返回 `_bstr_t` 中的字符数，但不包括封装的 `BSTR` 的终止 null 字符。

## <a name="syntax"></a>语法

```
unsigned int length ( ) const throw( );
```

## <a name="remarks"></a>备注

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_bstr_t 类](../cpp/bstr-t-class.md)