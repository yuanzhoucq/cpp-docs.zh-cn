---
title: is_nothrow_default_constructible 类
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_default_constructible
helpviewer_keywords:
- is_nothrow_default_constructible
ms.assetid: c576fcc9-5be1-43aa-b93a-64d3f1848887
ms.openlocfilehash: d635c8a06d3acc45d214dbe7cb1eb7800f56dc86
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148479"
---
# <a name="isnothrowdefaultconstructible-class"></a>is_nothrow_default_constructible 类

测试类型是否具有非引发默认构造函数。

## <a name="syntax"></a>语法

```cpp
template <class Ty>
struct is_nothrow_default_constructible;
```

### <a name="parameters"></a>参数

*Ty*<br/>
要查询的类型。

## <a name="remarks"></a>备注

如果类型谓词的实例将保留 true 类型*Ty*具有 nothrow 默认构造函数，否则为 false。 类型谓词的实例等效于 `is_nothrow_constructible<Ty>`。

## <a name="requirements"></a>要求

**标头：**\<type_traits>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
