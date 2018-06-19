---
title: is_standard_layout 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_standard_layout
dev_langs:
- C++
helpviewer_keywords:
- is_standard_layout class
- is_standard_layout
ms.assetid: 15ccf111-f537-45ef-b552-59152a7ba312
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d899d9c56ecc8b27b18498de225bbba6f0d110d2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33852079"
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
|`Ty`|要查询的类型|

## <a name="remarks"></a>备注

如果类型 `Ty` 是具有内存中成员对象的标准布局的类，则此类型谓词的实例为 true；否则为 false。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
