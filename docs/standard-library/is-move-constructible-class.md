---
title: is_move_constructible 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- type_traits/std::is_move_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 35e7bb78b1d2f2bc228230ef7d543aabb4506ae8
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="ismoveconstructible-class"></a>is_move_constructible 类

测试类型是否具有移动构造函数。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>参数

要进行求值的 T 类型

## <a name="remarks"></a>备注

如果类型 `T` 可通过使用移动操作构造，则类型谓词的计算结果为 true。 此谓词等效于 `is_constructible<T, T&&>`。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
