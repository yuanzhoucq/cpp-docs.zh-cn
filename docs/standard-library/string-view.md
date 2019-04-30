---
title: '&lt;string_view&gt;'
ms.date: 04/18/2019
helpviewer_keywords:
- string_view header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
ms.openlocfilehash: 8952416cf37fc4d8d281d6ced9b8264495ec3799
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346975"
---
# <a name="ltstringviewgt"></a>&lt;string_view&gt;

定义类模板`basic_string_view`和相关类型和运算符。 (需要编译器选项[/std: c + + 17](../build/reference/std-specify-language-standard-version.md)或更高版本。)

## <a name="syntax"></a>语法

```cpp
#include <string_view>
```

## <a name="remarks"></a>备注

String_view 系列模板专用化提供了用于将只读的异常安全，不具有所有权的句柄传递给任何类似于字符串的对象的位置 0 处的序列的第一个元素的字符数据的有效方法。 函数参数的类型`string_view`(即的 typedef `basic_string_view<char>`) 可接受参数如`std::string`， **char\***，或为其窄字符的任何其他字符串类似于类隐式转换为`string_view`定义。 同样，参数`wstring_view`，`u16string_view`或`u32string_view`可以接受的隐式转换为其定义任何字符串类型。 有关详细信息，请参阅[basic_string_view 类](../standard-library/basic-string-view-class.md)。

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[string_view](../standard-library/string-view-typedefs.md#string_view)|类模板的专用化`basic_string_view`类型的元素**char**。|
|[wstring_view](../standard-library/string-view-typedefs.md#wstring_view)|类模板的专用化`basic_string_view`类型的元素**wchar_t**。|
|[u16string_view](../standard-library/string-view-typedefs.md#u16string_view)|类模板的专用化`basic_string_view`类型的元素`char16_t`。|
|[u32string_view](../standard-library/string-view-typedefs.md#u32string_view)|类模板的专用化`basic_string_view`类型的元素`char32_t`。|

### <a name="operators"></a>运算符

\<String_view > 比较运算符可以`string_view`对象与对象的任何可转换为字符串类型。

|运算符|描述|
|-|-|
|[operator!=](../standard-library/string-view-operators.md#op_neq)|测试运算符左侧的对象是否不等于右侧的对象。|
|[operator==](../standard-library/string-view-operators.md#op_eq_eq)|测试运算符左侧的对象是否等于右侧的对象。|
|[operator<](../standard-library/string-view-operators.md#op_lt)|测试运算符左侧的对象是否小于右侧的对象。|
|[operator<=](../standard-library/string-view-operators.md#op_lt_eq)|测试运算符左侧的对象是否小于或等于右侧的对象。|
|[operator<\<](../standard-library/string-view-operators.md#op_lt_lt)|将插入一个模板函数`string_view`到输出流。|
|[operator>](../standard-library/string-view-operators.md#op_gt)|测试运算符左侧的对象是否大于右侧的对象。|
|[operator>=](../standard-library/string-view-operators.md#op_gt_eq)|测试运算符左侧的对象是否大于或等于右侧的对象。|

### <a name="literals"></a>文本

|运算符|描述|
|-|-|
|[sv](../standard-library/string-view-operators.md#op_sv)|构造`string_view`， `wstring_view`， `u16string_view`，或`u32string_view`根据追加到字符串文字的类型。|

### <a name="classes"></a>类

|类|描述|
|-|-|
|[basic_string_view 类](../standard-library/basic-string-view-class.md)|类模板来提供到序列中的任意字符类对象的只读视图。|
|[hash](string-view-hash.md)|生成 string_view 的哈希值的函数对象。|

## <a name="requirements"></a>要求

- **标头：** \<string_view >

- **命名空间：** std

- **编译器选项：** /std: c + + 17 （或更高版本）

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
