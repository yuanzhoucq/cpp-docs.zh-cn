---
title: is_literal_type 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_literal_type
helpviewer_keywords:
- is_literal_type
ms.assetid: a03a4ebb-ee66-48d6-91bb-41cf72b2401f
ms.openlocfilehash: 804ef0462308b967fc0c4c95d8dfa96476475aab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62336462"
---
# <a name="isliteraltype-class"></a>is_literal_type 类

测试类型是否可充当 `constexpr` 变量，或者 `constexpr` 函数是否可以构造、使用或返回该类型。

## <a name="syntax"></a>语法

```cpp
template <class T>
struct is_literal_type;
```

### <a name="parameters"></a>参数

*T*<br/>
要查询的类型。

## <a name="remarks"></a>备注

如果类型谓词的实例将保留 true 类型*T*是*文本类型*，否则为 false。 文本类型为**void**，标量类型、 引用类型、 参数类型的数组或文本类类型。 文本类类型是一种类类型，其具有普通析构函数，为聚合类型或至少具有一个非移动非复制的 `constexpr` 构造函数，其所有基类和非静态数据成员为非易失性文本类型。 尽管文本类型始终为文本类型，但是文本类型的概念包括编译器在编译时可计算为 `constexpr` 的任何内容。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
