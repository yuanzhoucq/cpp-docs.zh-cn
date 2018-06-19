---
title: is_trivially_copyable 类 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_copyable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_copyable
ms.assetid: 89a53bf8-036c-4108-91e1-fe34adbde8b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 177ba6e688f6d7ed2b4c76eb0ede95cc288b1d5d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857527"
---
# <a name="istriviallycopyable-class"></a>is_trivially_copyable 类

测试类型是否为普通复制类型。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct is_trivially_copyable;
```

### <a name="parameters"></a>参数

`T` 查询的类型。

## <a name="remarks"></a>备注

如果类型 `T` 是普通复制类型，则类型谓词的实例为 true；否则为 false。 普通复制类型不具有任何重要的复制操作、移动操作或析构函数。 一般而言，如果复制操作可作为按位复制实现，则可将其视为普通复制。 内置类型和普通复制类型数组都可进行普通复制。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
