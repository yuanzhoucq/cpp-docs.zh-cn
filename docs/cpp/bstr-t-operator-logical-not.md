---
title: _bstr_t::operator ! | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::operator!
dev_langs:
- C++
helpviewer_keywords:
- '! operator'
- operator!, bstr
- operator !, bstr
ms.assetid: 6e60b5a5-2d28-4eec-9e12-790da8f1fdd4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a69bd0245035191f95f874bb6a4383c2e148e0a9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070835"
---
# <a name="bstrtoperator-"></a>_bstr_t::operator !

**Microsoft 专用**

检查封装`BSTR`是一个 NULL 字符串。

## <a name="syntax"></a>语法

```
bool operator!( ) const throw( );
```

## <a name="return-value"></a>返回值

如果是，则返回 TRUE，如果没有，则返回 FALSE。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_bstr_t 类](../cpp/bstr-t-class.md)