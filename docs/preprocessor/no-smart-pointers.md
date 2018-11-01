---
title: no_smart_pointers
ms.date: 11/04/2016
f1_keywords:
- no_search_pointers
helpviewer_keywords:
- no_smart_pointers attribute
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
ms.openlocfilehash: 305c08497a600f602767496cba48d108335fdeb8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636977"
---
# <a name="nosmartpointers"></a>no_smart_pointers
**C + + 专用**

取消对类型库中所有接口的智能指针的创建。

## <a name="syntax"></a>语法

```
no_smart_pointers
```

## <a name="remarks"></a>备注

默认情况下，当使用 `#import` 时，您将获得针对类型库中的所有接口的智能指针声明。 这些智能指针都是类型[_com_ptr_t 类](../cpp/com-ptr-t-class.md)。

**结束 c + + 专用**

## <a name="see-also"></a>请参阅

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指令](../preprocessor/hash-import-directive-cpp.md)