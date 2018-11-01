---
title: '&lt;system_error&gt; typedef'
ms.date: 11/04/2016
f1_keywords:
- system_error/std::generic_errno
ms.assetid: 28cf9f7d-9c28-4baa-a297-67c8260b07fb
ms.openlocfilehash: 95b2cb22d4fbff4f92cf28041e70ae599c318cbc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531046"
---
# <a name="ltsystemerrorgt-typedefs"></a>&lt;system_error&gt; typedef

||
|-|
|[generic_errno](#generic_errno)|

## <a name="generic_errno"></a>  generic_errno

一种表示枚举的类型，用于为所有由 `<errno.h>` 中的 Posix 定义的错误代码宏提供符号名称。

```cpp
typedef errc generic_error;
```

### <a name="remarks"></a>备注

该类型是 [errc](../standard-library/system-error-enums.md#errc) 的同义词。

## <a name="see-also"></a>请参阅

[<system_error>](../standard-library/system-error.md)<br/>
