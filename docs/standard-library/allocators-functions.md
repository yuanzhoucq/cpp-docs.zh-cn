---
title: '&lt;allocators&gt; 宏'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::ALLOCATOR_DECL
- allocators/std::CACHE_CHUNKLIST
- allocators/std::CACHE_FREELIST
- allocators/std::CACHE_SUBALLOC
- allocators/std::SYNC_DEFAULT
ms.assetid: 9cb5ee07-1ff9-4594-ae32-3c8c6efb511a
helpviewer_keywords:
- std::ALLOCATOR_DECL [C++]
- std::CACHE_CHUNKLIST [C++]
- std::CACHE_FREELIST [C++]
- std::CACHE_SUBALLOC [C++]
- std::SYNC_DEFAULT [C++]
ms.openlocfilehash: a8b988511d0cdd46ae7f41bce29eb26f593a57c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364973"
---
# <a name="ltallocatorsgt-macros"></a>&lt;allocators&gt; 宏

||||
|-|-|-|
|[ALLOCATOR_DECL](#allocator_decl)|[CACHE_CHUNKLIST](#cache_chunklist)|[CACHE_FREELIST](#cache_freelist)|
|[CACHE_SUBALLOC](#cache_suballoc)|[SYNC_DEFAULT](#sync_default)|

## <a name="allocator_decl"></a><a name="allocator_decl"></a>ALLOCATOR_DECL

生成分配器类模板。

```cpp
#define ALLOCATOR_DECL(cache, sync, name) <alloc_template>
```

### <a name="remarks"></a>备注

宏生成一个模板定义`template <class Type> class name {.....}`和一个`template <> class name<void> {.....}`专门化，它们共同定义一个分配器类模板，`sync`该模板使用同步筛选器`cache`和类型的缓存。

对于可以编译重新绑定的编译器，其生成的模板定义如下所示：

```cpp
struct rebind
   {    /* convert a name<Type> to a name<Other> */
   typedef name<Other> other;
   };
```

对于无法编译重新绑定的编译器，其生成的模板定义如下所示：

```cpp
template <class Type<class name
    : public stdext::allocators::allocator_base<Type,
    sync<stdext::allocators::rts_alloc<cache>>>
{
public:
    name() {}
    template <class Other>
    name(const name<Other>&) {}
    template <class Other>
    name& operator= (const name<Other>&)
    {
        return *this;
    }
};
```

## <a name="cache_chunklist"></a><a name="cache_chunklist"></a>CACHE_CHUNKLIST

生成 `stdext::allocators::cache_chunklist<sizeof(Type)>`。

```cpp
#define CACHE_CHUNKLIST <cache_class>
```

### <a name="remarks"></a>备注

## <a name="cache_freelist"></a><a name="cache_freelist"></a>CACHE_FREELIST

生成 `stdext::allocators::cache_freelist<sizeof(Type), max>`。

```cpp
#define CACHE_FREELIST(max) <cache_class>
```

### <a name="remarks"></a>备注

## <a name="cache_suballoc"></a><a name="cache_suballoc"></a>CACHE_SUBALLOC

生成 `stdext::allocators::cache_suballoc<sizeof(Type)>`。

```cpp
#define CACHE_SUBALLOC <cache_class>
```

### <a name="remarks"></a>备注

## <a name="sync_default"></a><a name="sync_default"></a>SYNC_DEFAULT

生成同步筛选器。

```cpp
#define SYNC_DEFAULT <sync_template>
```

### <a name="remarks"></a>备注

如果编译器支持编译单线程和多线程应用程序，则对于单线程应用程序，宏生成 `stdext::allocators::sync_none`；在所有其他情况下生成 `stdext::allocators::sync_shared`。

## <a name="see-also"></a>另请参阅

[\<分配器>](../standard-library/allocators-header.md)
