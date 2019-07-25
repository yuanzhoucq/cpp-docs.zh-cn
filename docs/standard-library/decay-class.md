---
title: decay 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::decay
helpviewer_keywords:
- decay class
ms.assetid: 96baa2fd-c8e0-49af-be91-ba375ba7f9dc
ms.openlocfilehash: 73b9e2d8ef9a14830c13ee3f6566137bb51e939d
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450642"
---
# <a name="decay-class"></a>decay 类

生成按值传递的类型。 将类型设置为非引用、非常量、非易失，或者使指针从一个函数或数组类型指向该类型。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct decay;

template <class T>
using decay_t = typename decay<T>::type;
```

### <a name="parameters"></a>参数

*关心*\
要修改的类型。

## <a name="remarks"></a>备注

Decay 模板用于生成结果的类型，就像按值作为参数传递的类型。 模板类成员 typedef `type` 包含在以下几个阶段中定义的修改类型：

- 类型 `U` 定义为 `remove_reference<T>::type`。

- 如果`is_array<U>::value`为 true，则修改的类型 `type` 是 `remove_extent<U>::type *`。

- 否则，如果 `is_function<U>::value` 为 true，则修改的类型 `type` 是 `add_pointer<U>::type`。

- 否则，修改的类型 `type` 是 `remove_cv<U>::type`。

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)
