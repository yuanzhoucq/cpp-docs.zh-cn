---
title: discard_block_engine 类 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::discard_block_engine
dev_langs:
- C++
helpviewer_keywords:
- discard_block_engine class
ms.assetid: aa84808e-38fe-4fa0-9f73-d5b9a653345b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b814f64f340577508add6bf3c0f85ffac0786db7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33843465"
---
# <a name="discardblockengine-class"></a>discard_block_engine 类

通过丢弃由其基引擎返回的值，生成随机序列。

## <a name="syntax"></a>语法

```cpp
template <class Engine, size_t P, size_t R>
class discard_block_engine;
```

### <a name="parameters"></a>参数

`Engine` 基引擎类型中。

`P` **块大小**。 每个块中的值数。

`R` **已用的块**。 已使用的每个块中的值数。 丢弃剩余部分 ( `P` - `R`)。 **前提条件**：`0 < R ≤ P`

## <a name="members"></a>成员

||||
|-|-|-|
|`discard_block_engine::discard_block_engine`|`discard_block_engine::base`|`discard_block_engine::discard`|
|`discard_block_engine::operator()`|`discard_block_engine::base_type`|`discard_block_engine::seed`|

有关引擎成员的详细信息，请参阅 [\<random>](../standard-library/random.md)。

## <a name="remarks"></a>备注

此模板类描述了通过弃用由其基引擎返回的一些值来产生值的引擎适配器。

## <a name="requirements"></a>要求

**标头：**\<random>

**命名空间：** std

## <a name="see-also"></a>请参阅

[\<random>](../standard-library/random.md)<br/>
