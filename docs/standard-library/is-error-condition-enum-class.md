---
title: is_error_condition_enum 类
ms.date: 11/04/2016
f1_keywords:
- system_error/std::is_error_condition_enum
helpviewer_keywords:
- is_error_condition_enum class
ms.assetid: 752bb87a-c61c-4304-9254-5aaf228b59c0
ms.openlocfilehash: 213970d6260eaf55ac1bd678e6317cf2346ed9bc
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245169"
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

## <a name="see-also"></a>请参阅

[<type_traits>](../standard-library/type-traits.md)<br/>
