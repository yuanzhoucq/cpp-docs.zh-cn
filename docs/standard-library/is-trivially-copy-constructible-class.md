---
title: is_trivially_copy_constructible 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copy_constructible
helpviewer_keywords:
- is_trivially_copy_constructible
ms.assetid: 4274cef5-afdd-4f2d-bc83-7562e7944ddf
ms.openlocfilehash: aa6d6b19ae2bd5d6967c57db61c5697c0c6153e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630511"
---
# <a name="istriviallycopyconstructible-class"></a>is_trivially_copy_constructible 类

测试类型是否包含普通复制构造函数。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct is_trivially_copy_constructible;
```

### <a name="parameters"></a>参数

*T*<br/>
要查询的类型。

## <a name="remarks"></a>备注

如果类型谓词的实例将保留 true 类型*T*是一个类具有普通复制构造函数，否则为 false。

一个类的复制构造函数*T*并不重要，如果它隐式声明的该类*T*没有虚函数或虚拟基，类的所有直接基*T*具有普通复制构造函数的类类型的所有非静态数据成员的类具有普通复制构造函数和类的类型数组的所有非静态数据成员的类具有普通复制构造函数。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
