---
title: is_trivial 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivial
helpviewer_keywords:
- is_trivial
ms.assetid: 6beb11d4-2f38-4c7e-9959-ca5d26250df7
ms.openlocfilehash: 609fdd9c3d0d00eea607db4aefd31163234a9a00
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526849"
---
# <a name="istrivial-class"></a>is_trivial 类

测试类型是否为通常类型。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct is_trivial;
```

### <a name="parameters"></a>参数

*T*<br/>
要查询的类型。

## <a name="remarks"></a>备注

如果类型谓词的实例将保留 true 类型*T*是简单类型，否则为 false。 常用类型是标量类型、完全可复制类类型、这些类型的数组以及这些类型的 cv 限定版本。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
