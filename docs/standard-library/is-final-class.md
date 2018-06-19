---
title: is_final 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_final
dev_langs:
- C++
helpviewer_keywords:
- is_final
ms.assetid: 9dbad82f-6685-4909-94e8-98e4a93994b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b3d2c37b73d79619aeb16e7b1b81ad71819b09b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33844050"
---
# <a name="isfinal-class"></a>is_final 类

测试类型是否是标记为 `final` 的类类型。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct is_final;
```

### <a name="parameters"></a>参数

`T` 查询的类型。

## <a name="remarks"></a>备注

如果类型 `T` 是标记为 `final` 的类类型，则类型谓词的实例为 true；否则为 false。 如果 `T` 是类类型，则其必须是完整类型。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
[final 说明符](../cpp/final-specifier.md)<br/>
