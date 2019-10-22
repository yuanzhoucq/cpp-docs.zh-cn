---
title: treat_as_floating_point 结构
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::treat_as_floating_point
ms.assetid: d0a2161c-bbb2-4924-8961-7568d5ad5434
ms.openlocfilehash: add69179b23a953a937458cbfa55254b21c5ea37
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72685116"
---
# <a name="treat_as_floating_point-structure"></a>treat_as_floating_point 结构

指定是否可将 `Rep` 视为浮点类型。

## <a name="syntax"></a>语法

```cpp
template <class Rep>
struct treat_as_floating_point : is_floating_point<Rep>;
```

## <a name="remarks"></a>备注

仅当专用化 `treat_as_floating_point<Rep>` 派生自 [true_type](../standard-library/type-traits-typedefs.md#true_type) 时，才可将 `Rep` 视为浮点类型。 类模板可专用于用户定义类型。

## <a name="requirements"></a>要求

**标头：** \<chrono >

**命名空间：** std::chrono

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)
