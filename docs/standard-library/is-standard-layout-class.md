---
title: is_standard_layout 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_standard_layout
helpviewer_keywords:
- is_standard_layout class
- is_standard_layout
ms.assetid: 15ccf111-f537-45ef-b552-59152a7ba312
ms.openlocfilehash: 4f999eaa4a5c1ea7e9672a5efdc6000a4d3d9759
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457415"
---
# <a name="isstandardlayout-class"></a>is_standard_layout 类

测试类型是否为标准布局。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_standard_layout;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*Ty*|要查询的类型|

## <a name="remarks"></a>备注

如果类型*Ty*是具有内存中成员对象的标准布局的类, 则此类型谓词的实例为 true; 否则为 false。

## <a name="requirements"></a>要求

**标头：** \<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)
