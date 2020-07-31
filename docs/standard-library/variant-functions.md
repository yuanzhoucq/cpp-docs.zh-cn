---
title: '&lt;变体 &gt; 函数'
ms.date: 04/04/2019
f1_keywords:
- variant/std::get
- variant/std::get_if
- variant/std::holds_alternative
- variant/std::visit
ms.openlocfilehash: b39e75cb94f8439bba802925e6145dcf67942960
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232828"
---
# <a name="ltvariantgt-functions"></a>&lt;变体 &gt; 函数

## <a name="get"></a><a name="get"></a>获取

获取对象的变体。

```cpp
template <size_t I, class... Types>
    constexpr variant_alternative_t<I, variant<Types...>>& get(variant<Types...>&);
template <size_t I, class... Types>
    constexpr variant_alternative_t<I, variant<Types...>>&& get(variant<Types...>&&);
template <size_t I, class... Types>
    constexpr const variant_alternative_t<I, variant<Types...>>& get(const variant<Types...>&);
template <size_t I, class... Types>
    constexpr const variant_alternative_t<I, variant<Types...>>&& get(const variant<Types...>&&);
template <class T, class... Types>
    constexpr T& get(variant<Types...>&);
template <class T, class... Types>
    constexpr T&& get(variant<Types...>&&);
template <class T, class... Types>
    constexpr const T& get(const variant<Types...>&);
template <class T, class... Types>
    constexpr const T&& get(const variant<Types...>&&);
```

## <a name="get_if"></a><a name="get_if"></a>get_if

获取对象的变体（如果存在）。

```cpp
template <size_t I, class... Types>
    constexpr add_pointer_t<variant_alternative_t<I, variant<Types...>>> get_if(variant<Types...>*) noexcept;
template <size_t I, class... Types>
    constexpr add_pointer_t<const variant_alternative_t<I, variant<Types...>>> get_if(const variant<Types...>*) noexcept;
template <class T, class... Types>
    constexpr add_pointer_t<T> get_if(variant<Types...>*) noexcept;
template <class T, class... Types>
    constexpr add_pointer_t<const T> get_if(const variant<Types...>*) noexcept;
```

## <a name="holds_alternative"></a><a name="holds_alternative"></a>holds_alternative

**`true`** 如果变量存在，则返回。

```cpp
template <class T, class... Types>
    constexpr bool holds_alternative(const variant<Types...>&) noexcept;
```

## <a name="swap"></a><a name="swap"></a>购

```cpp
template <class... Types>
    void swap(variant<Types...>&, variant<Types...>&) noexcept(see below);
```

## <a name="variant_npos"></a><a name="variant_npos"></a>variant_npos

```cpp
namespace std {
    inline constexpr size_t variant_npos = -1;
}
```

## <a name="visit"></a><a name="visit"></a>参阅

移到下一个**变体**。

```cpp
template <class Visitor, class... Variants>
    constexpr see below
        visit(Visitor&&, Variants&&...);
```
