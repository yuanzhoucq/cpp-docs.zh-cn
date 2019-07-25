---
title: shuffle_order_engine 类
ms.date: 11/04/2016
f1_keywords:
- random/std::shuffle_order_engine
- random/std::shuffle_order_engine::base
- random/std::shuffle_order_engine::discard
- random/std::shuffle_order_engine::operator()
- random/std::shuffle_order_engine::base_type
- random/std::shuffle_order_engine::seed
helpviewer_keywords:
- std::shuffle_order_engine [C++]
- std::shuffle_order_engine [C++], base
- std::shuffle_order_engine [C++], discard
- std::shuffle_order_engine [C++], base_type
- std::shuffle_order_engine [C++], seed
ms.assetid: 0bcd1fb0-44d7-4e59-bb1b-4a9b673a960d
ms.openlocfilehash: 972ba83afb5478cd89314817ba823b8d5657c9c8
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450415"
---
# <a name="shuffleorderengine-class"></a>shuffle_order_engine 类

通过对从其基引擎中返回的值进行重新排序，生成随机序列。

## <a name="syntax"></a>语法

```cpp
template <class Engine, size_t K>
class shuffle_order_engine;
```

### <a name="parameters"></a>参数

*搜索引擎优化*\
基引擎类型。

*温度*\
**表大小**。 缓冲区（表）中的元素数。 **前提条件**：`0 < K`

## <a name="members"></a>成员

||||
|-|-|-|
|`shuffle_order_engine::shuffle_order_engine`|`shuffle_order_engine::base`|`shuffle_order_engine::discard`|
|`shuffle_order_engine::operator()`|`shuffle_order_engine::base_type`|`shuffle_order_engine::seed`|

有关引擎成员的详细信息，请参阅 [\<random>](../standard-library/random.md)。

## <a name="remarks"></a>备注

此模板类描述了通过对其基引擎返回的值进行重新排序来产生值的引擎适配器。 每个构造函数使用基引擎返回的*K*值填充内部表, 并在请求值时从表中选择一个随机元素。

## <a name="requirements"></a>要求

**标头：** \<random>

**命名空间：** std

## <a name="see-also"></a>请参阅

[\<random>](../standard-library/random.md)
