---
title: underlying_type 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::underlying_type
helpviewer_keywords:
- underlying_type
ms.assetid: 691ddce3-2677-4480-bd35-d933fab85d3e
ms.openlocfilehash: ea4768d78047112a7584ca49b0e4487fad55a970
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688844"
---
# <a name="underlying_type-class"></a>underlying_type 类

生成枚举类型的基础整型类型。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct underlying_type;
```

### <a name="parameters"></a>参数

*T* \
要修改的类型。

## <a name="remarks"></a>备注

当*t*是枚举类型时，类模板的 `type` 成员 typedef 将命名*t*的基础整型类型，否则不会 `type` 成员 typedef。

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间:** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)
