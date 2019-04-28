---
title: '&lt;new&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
ms.openlocfilehash: 85c8d0c2974f734783e3d9c2ad1269f84d605dec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223631"
---
# <a name="ltnewgt-typedefs"></a>&lt;new&gt; typedefs

| |
| - |
|[new_handler](#new_handler)|

## <a name="new_handler"></a>new_handler

该类型指向适合用作新处理程序的函数。

```cpp
typedef void (*new_handler)();
```

### <a name="remarks"></a>备注

当它们不能满足额外存储的请求时，**operatornew** 或 `operator new[]` 将调用这种类型的处理程序函数。

### <a name="example"></a>示例

有关将 `new_handler` 用作返回值的示例，请参阅 [set_new_handler](../standard-library/new-functions.md#set_new_handler)。

## <a name="see-also"></a>请参阅

[\<new>](../standard-library/new.md)<br/>
