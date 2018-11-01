---
title: is_error_condition_enum 类
ms.date: 11/04/2016
f1_keywords:
- system_error/std::is_error_condition_enum
helpviewer_keywords:
- is_error_condition_enum class
ms.assetid: 752bb87a-c61c-4304-9254-5aaf228b59c0
ms.openlocfilehash: 1b5b55431db806bb109a58199ad9d2d7c16f38ff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612714"
---
# <a name="iserrorconditionenum-class"></a>is_error_condition_enum 类

表示测试 [error_condition](../standard-library/error-condition-class.md) 枚举的类型谓词。

## <a name="syntax"></a>语法

```cpp
template <_Enum>
class is_error_condition_enum;
```

## <a name="remarks"></a>备注

如果类型 `_Enum` 是一个适合存储在类型 `error_condition` 的对象中的枚举值，则此[类型谓词](../standard-library/type-traits.md)的实例为 true。

允许将专用化添加到此类型，以获得用户定义类型。

## <a name="requirements"></a>要求

**标头：** \<system_error>

**命名空间：** std

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
[<system_error>](../standard-library/system-error.md)<br/>
