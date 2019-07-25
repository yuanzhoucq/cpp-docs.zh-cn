---
title: underlying_type 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::underlying_type
helpviewer_keywords:
- underlying_type
ms.assetid: 691ddce3-2677-4480-bd35-d933fab85d3e
ms.openlocfilehash: 465383357e6c0306c24fe8325327327c3a3b64c1
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454976"
---
# <a name="underlyingtype-class"></a>underlying_type 类

生成枚举类型的基础整型类型。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct underlying_type;
```

### <a name="parameters"></a>参数

*关心*\
要修改的类型。

## <a name="remarks"></a>备注

当 t 是枚举类型时, 模板类的 `type` 成员typedef命名t的基础整型类型,否则没有成员`type` typedef。

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)
