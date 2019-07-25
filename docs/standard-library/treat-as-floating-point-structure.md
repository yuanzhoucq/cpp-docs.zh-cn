---
title: treat_as_floating_point 结构
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::treat_as_floating_point
ms.assetid: d0a2161c-bbb2-4924-8961-7568d5ad5434
ms.openlocfilehash: 4cf3ac5be972d8636f1d3dbda3b195f4012517be
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459887"
---
# <a name="treatasfloatingpoint-structure"></a>treat_as_floating_point 结构

指定是否可将 `Rep` 视为浮点类型。

## <a name="syntax"></a>语法

```cpp
template <class Rep>
struct treat_as_floating_point : is_floating_point<Rep>;
```

## <a name="remarks"></a>备注

仅当专用化 `treat_as_floating_point<Rep>` 派生自 [true_type](../standard-library/type-traits-typedefs.md#true_type) 时，才可将 `Rep` 视为浮点类型。 此模板类可专用于用户定义的类型。

## <a name="requirements"></a>要求

**标头:** \<chrono >

**命名空间：** std::chrono

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)
