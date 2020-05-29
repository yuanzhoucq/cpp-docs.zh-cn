---
title: short_vector 结构
ms.date: 11/04/2016
f1_keywords:
- short_vector
- AMP_SHORT_VECTORS/short_vector
- AMP_SHORT_VECTORS/Concurrency::graphics::short_vector::short_vector Constructor
ms.assetid: e4f50b8f-1150-437d-b58c-79c5fb883708
ms.openlocfilehash: fc2864477da80885b18dabb08b9ccbee30f31387
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374753"
---
# <a name="short_vector-structure"></a>short_vector 结构

short_vector 提供可广泛用于短矢量编程的元编程定义。

## <a name="syntax"></a>语法

```cpp
template<
    typename _Scalar_type,
    int _Size
>
struct short_vector;
template<>
struct short_vector<unsigned int, 1>;
template<>
struct short_vector<unsigned int, 2>;
template<>
struct short_vector<unsigned int, 3>;
template<>
struct short_vector<unsigned int, 4>;
template<>
struct short_vector<int, 1>;
template<>
struct short_vector<int, 2>;
template<>
struct short_vector<int, 3>;
template<>
struct short_vector<int, 4>;
template<>
struct short_vector<float, 1>;
template<>
struct short_vector<float, 2>;
template<>
struct short_vector<float, 3>;
template<>
struct short_vector<float, 4>;
template<>
struct short_vector<unorm, 1>;
template<>
struct short_vector<unorm, 2>;
template<>
struct short_vector<unorm, 3>;
template<>
struct short_vector<unorm, 4>;
template<>
struct short_vector<norm, 1>;
template<>
struct short_vector<norm, 2>;
template<>
struct short_vector<norm, 3>;
template<>
struct short_vector<norm, 4>;
template<>
struct short_vector<double, 1>;
template<>
struct short_vector<double, 2>;
template<>
struct short_vector<double, 3>;
template<>
struct short_vector<double, 4>;
```

### <a name="parameters"></a>参数

*_Scalar_type*<br/>

*_Size*<br/>

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|`type`||

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[short_vector::short_vector 构造函数](#ctor)||

## <a name="inheritance-hierarchy"></a>继承层次结构

`short_vector`

## <a name="requirements"></a>要求

**标题：** amp_short_vectors.h

**命名空间：** 并发：：图形

## <a name="short_vectorshort_vector-constructor"></a><a name="ctor"></a>short_vector：short_vector构造函数

```cpp
short_vector();
```

## <a name="see-also"></a>另请参阅

[Concurrency::graphics 命名空间](concurrency-graphics-namespace.md)
