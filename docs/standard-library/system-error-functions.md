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
ms.openlocfilehash: 78be83af678b553babbf1cde3d96c1507940b611
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412106"
---
# <a name="ltsystemerrorgt-functions"></a>&lt;system_error&gt; 函数

||||
|-|-|-|
|[generic_category](#generic_category)|[make_error_code](#make_error_code)|[make_error_condition](#make_error_condition)|
|[system_category](#system_category)|||

## <a name="generic_category"></a> generic_category

表示一般错误的类别。

```cpp
const error_category& generic_category() noexcept;
```

### <a name="remarks"></a>备注

`generic_category`对象是实现[error_category](../standard-library/error-category-class.md)。

## <a name="make_error_code"></a>make_error_code

创建错误代码对象。

```cpp
error_code make_error_code(std::errc error) noexcept;
```

### <a name="parameters"></a>参数

*error*\
`std::errc`要存储的错误代码对象中的枚举值。

### <a name="return-value"></a>返回值

错误代码对象。

### <a name="remarks"></a>备注

## <a name="make_error_condition"></a>make_error_condition

创建错误条件对象。

```cpp
error_condition make_error_condition(std::errc error) noexcept;
```

### <a name="parameters"></a>参数

*error*\
`std::errc`要存储的错误代码对象中的枚举值。

### <a name="return-value"></a>返回值

错误条件对象。

### <a name="remarks"></a>备注

## <a name="system_category"></a>  system_category

表示因低级别系统溢出而引起的错误类别。

```cpp
const error_category& system_category() noexcept;
```

### <a name="remarks"></a>备注

`system_category`对象是实现[error_category](../standard-library/error-category-class.md)。

## <a name="see-also"></a>请参阅

[\<system_error>](../standard-library/system-error.md)<br/>
