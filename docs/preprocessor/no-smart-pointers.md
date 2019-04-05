---
title: no_smart_pointers
ms.date: 11/04/2016
f1_keywords:
- no_search_pointers
helpviewer_keywords:
- no_smart_pointers attribute
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
ms.openlocfilehash: ed4950b9e90ef968fcf0c42e4f0a9775c58ea7ec
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59030162"
---
# <a name="nosmartpointers"></a>no_smart_pointers
**C++ 专用**

取消对类型库中所有接口的智能指针的创建。

## <a name="syntax"></a>语法

```
no_smart_pointers
```

## <a name="remarks"></a>备注

默认情况下，当使用 `#import` 时，您将获得针对类型库中的所有接口的智能指针声明。 这些智能指针都是类型[_com_ptr_t 类](../cpp/com-ptr-t-class.md)。

**结束 C++ 专用**

## <a name="see-also"></a>请参阅

[#import 特性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指令](../preprocessor/hash-import-directive-cpp.md)