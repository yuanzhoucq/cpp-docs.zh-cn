---
title: uses_allocator 结构
ms.date: 11/04/2016
f1_keywords:
- future/std::uses_allocator
ms.assetid: c418f002-62e9-4806-b70c-41c663cae583
ms.openlocfilehash: 4dc0094d46c005e4af62924bc785a05b3ca43090
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454673"
---
# <a name="usesallocator-structure"></a>uses_allocator 结构

始终为 true 的专用化。

## <a name="syntax"></a>语法

```cpp
template <class Ty, class Alloc>
struct uses_allocator<promise<Ty>, Alloc> : true_type;
template <class Ty, class Alloc>
struct uses_allocator<packaged_task<Ty>, Alloc> : true_type;
```

## <a name="requirements"></a>要求

**标头:** \<未来 >

**命名空间：** std

## <a name="specializations"></a>专用化

### <a name="tuple"></a>\<元组 >

```cpp
template <class... Types, class Alloc>
struct uses_allocator<tuple<Types...>, Alloc>;
```

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[\<future>](../standard-library/future.md)
