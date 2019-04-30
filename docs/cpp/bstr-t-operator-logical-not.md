---
title: _bstr_t::operator !
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::operator!
helpviewer_keywords:
- '! operator'
- operator!, bstr
- operator !, bstr
ms.assetid: 6e60b5a5-2d28-4eec-9e12-790da8f1fdd4
ms.openlocfilehash: 3be0ad19260c5b68894e28861ed5bc1635ef4c79
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389237"
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