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
ms.openlocfilehash: 6223151acbce299178101735db05f7b4bd516f2f
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965508"
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

此类型谓词的实例保留为 true 如果类型*Ty*是具有成员对象的标准布局在内存中，否则为 false 的类。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
