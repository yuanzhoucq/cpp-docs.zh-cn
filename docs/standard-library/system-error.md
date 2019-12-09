---
title: '&lt;system_error&gt;'
ms.date: 03/15/2019
f1_keywords:
- <system_error>
- system_error
helpviewer_keywords:
- system_error header
ms.assetid: 5e046c6e-48d9-4740-8c8a-05f3727c1215
ms.openlocfilehash: b9ddb3117afe37060b8013be235bdb11a2a031ac
ms.sourcegitcommit: 6ddfb8be5e5923a4d90a2c0f93f76a27ce7ac299
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/06/2019
ms.locfileid: "74898852"
---
# <a name="ltsystem_errorgt"></a>&lt;system_error&gt;

包括标头 \<system_error > 定义异常类 `system_error` 和相关模板来处理低级别系统错误。

## <a name="requirements"></a>需求

**标头：** \<system_error>

**命名空间:** std

## <a name="members"></a>Members

### <a name="objects"></a>对象

|||
|-|-|
|[generic_category](../standard-library/system-error-functions.md#generic_category)|表示一般错误的类别。|
|[is_error_code_enum_v](../standard-library/system-error-functions.md#is_error_code_enum_v)||
|[is_error_condition_enum_v](../standard-library/system-error-functions.md#is_error_condition_enum_v)||
|[system_category](../standard-library/system-error-functions.md#system_category)|表示因低级别系统溢出而引起的错误类别。|

### <a name="functions"></a>函数

|||
|-|-|
|[make_error_code](../standard-library/system-error-functions.md#make_error_code)|创建一个 `error_code` 对象。|
|[make_error_condition](../standard-library/system-error-functions.md#make_error_condition)|创建一个 `error_condition` 对象。|

### <a name="operators"></a>运算符

|||
|-|-|
|[operator==](../standard-library/system-error-operators.md#op_eq_eq)|测试运算符左侧的对象是否等于右侧的对象。|
|[operator!=](../standard-library/system-error-operators.md#op_neq)|测试运算符左侧的对象是否不等于右侧的对象。|
|[operator<](../standard-library/system-error-operators.md#op_lt)|测试一个对象是否小于要比较的传入对象。|
|[operator<<](../standard-library/system-error-operators.md#op_ostream)||

### <a name="enums"></a>枚举

|||
|-|-|
|[errc](../standard-library/system-error-enums.md#errc)|为 `<errno.h>`中的 POSIX 定义的所有错误代码宏提供符号名称。|

### <a name="classes-and-structs"></a>类和结构

|||
|-|-|
|[error_category](../standard-library/error-category-class.md)|表示描述错误代码类别的对象的抽象、公用基。|
|[error_code](../standard-library/error-code-class.md)|表示特定于实现的低级别系统错误。|
|[error_condition](../standard-library/error-condition-class.md)|表示用户定义的错误代码。|
|[hash](../standard-library/hash-structure.md#system_error)||
|[is_error_code_enum](../standard-library/is-error-code-enum-class.md)|表示测试 [error_code](../standard-library/error-code-class.md) 枚举的类型谓词。|
|[is_error_condition_enum](../standard-library/is-error-condition-enum-class.md)|表示测试 [error_condition Class](../standard-library/error-condition-class.md) 枚举的类型谓词。|
|[system_error](../standard-library/system-error-class.md)|表示为报告低级别系统溢出而引发的所有异常的基类。|

## <a name="see-also"></a>另请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)
