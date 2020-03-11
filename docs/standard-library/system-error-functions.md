---
title: '&lt;system_error&gt; 函数'
ms.date: 03/15/2019
f1_keywords:
- system_error/std::generic_category
- system_error/std::make_error_code
- system_error/std::make_error_condition
- system_error/std::system_category
ms.assetid: 57d6f15f-f0b7-4e2f-80fe-31d3c320ee33
helpviewer_keywords:
- std::generic_category
- std::make_error_code
- std::make_error_condition
- std::system_category
ms.openlocfilehash: ab4d0d1ee810df8f719bba762262eb03bf899408
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876250"
---
# <a name="ltsystem_errorgt-functions"></a>&lt;system_error&gt; 函数

## <a name="generic_category"></a>generic_category

表示一般错误的类别。

```cpp
const error_category& generic_category() noexcept;
```

### <a name="remarks"></a>备注

`generic_category` 对象是[error_category](../standard-library/error-category-class.md)的实现。

## <a name="is_error_code_enum_v"></a>is_error_code_enum_v

```cpp
template <class T> 
    inline constexpr bool is_error_code_enum_v = is_error_code_enum<T>::value;
```

## <a name="is_error_condition_enum_v"></a>is_error_condition_enum_v

```cpp
template <class T> 
    inline constexpr bool is_error_condition_enum_v = is_error_condition_enum<T>::value;
```

## <a name="make_error_code"></a>make_error_code

创建错误代码对象。

```cpp
error_code make_error_code(std::errc error) noexcept;
```

### <a name="parameters"></a>parameters

*错误*\
要存储在错误代码对象中的 `std::errc` 枚举值。

### <a name="return-value"></a>返回值

错误代码对象。

### <a name="remarks"></a>备注

## <a name="make_error_condition"></a>make_error_condition

创建错误条件对象。

```cpp
error_condition make_error_condition(std::errc error) noexcept;
```

### <a name="parameters"></a>parameters

*错误*\
要存储在错误代码对象中的 `std::errc` 枚举值。

### <a name="return-value"></a>返回值

错误条件对象。

### <a name="remarks"></a>备注

## <a name="system_category"></a>system_category

表示因低级别系统溢出而引起的错误类别。

```cpp
const error_category& system_category() noexcept;
```

### <a name="remarks"></a>备注

`system_category` 对象是[error_category](../standard-library/error-category-class.md)的实现。
