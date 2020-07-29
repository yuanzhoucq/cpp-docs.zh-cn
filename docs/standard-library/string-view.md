---
title: '&lt;string_view&gt;'
ms.date: 04/18/2019
helpviewer_keywords:
- string_view header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
ms.openlocfilehash: 13b6f5c63b9426fc4c31527f0d1ae8291d07807f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222207"
---
# <a name="ltstring_viewgt"></a>&lt;string_view&gt;

定义类模板 `basic_string_view` 以及相关类型和运算符。 （需要编译器选项[std： c + + 17](../build/reference/std-specify-language-standard-version.md)或更高版本。）

## <a name="syntax"></a>语法

```cpp
#include <string_view>
```

## <a name="remarks"></a>备注

String_view 系列模板专用化提供了一种有效的方法，可将只读、异常安全、非拥有的句柄传递给任何类似于字符串的对象，并将其序列的第一个元素置于位置零。 类型为 `string_view` （是的 typedef）的函数参数 `basic_string_view<char>` 可以接受参数，如 `std::string` 、 **char \* **或为其定义了隐式转换的任何其他类似于字符串的窄字符类 `string_view` 。 同样，或的参数 `wstring_view` 也 `u16string_view` `u32string_view` 可以接受为其定义了隐式转换的任何字符串类型。 有关详细信息，请参阅[Basic_string_view 类](../standard-library/basic-string-view-class.md)。

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[string_view](../standard-library/string-view-typedefs.md#string_view)|类模板的专用化 `basic_string_view` ，其中包含类型的元素 **`char`** 。|
|[wstring_view](../standard-library/string-view-typedefs.md#wstring_view)|类模板的专用化 `basic_string_view` ，其中包含类型的元素 **`wchar_t`** 。|
|[u16string_view](../standard-library/string-view-typedefs.md#u16string_view)|类模板的专用化 `basic_string_view` ，其中包含类型的元素 **`char16_t`** 。|
|[u32string_view](../standard-library/string-view-typedefs.md#u32string_view)|类模板的专用化 `basic_string_view` ，其中包含类型的元素 **`char32_t`** 。|

### <a name="operators"></a>运算符

\<string_view>运算符可以将 `string_view` 对象与任何可转换的字符串类型的对象进行比较。

|操作员|说明|
|-|-|
|[operator！ =](../standard-library/string-view-operators.md#op_neq)|测试运算符左侧的对象是否不等于右侧的对象。|
|[operator = =](../standard-library/string-view-operators.md#op_eq_eq)|测试运算符左侧的对象是否等于右侧的对象。|
|[运算符<](../standard-library/string-view-operators.md#op_lt)|测试运算符左侧的对象是否小于右侧的对象的位置。|
|[运算符<=](../standard-library/string-view-operators.md#op_lt_eq)|测试运算符左侧的对象是否小于或等于右侧的对象。|
|[运算符<\<](../standard-library/string-view-operators.md#op_lt_lt)|将插入 `string_view` 到输出流中的模板函数。|
|[运算符>](../standard-library/string-view-operators.md#op_gt)|测试运算符左侧的对象是否大于右侧的对象的位置。|
|[运算符>=](../standard-library/string-view-operators.md#op_gt_eq)|测试运算符左侧的对象是否大于或等于右侧的对象。|

### <a name="literals"></a>文字

|操作员|说明|
|-|-|
|[sv](../standard-library/string-view-operators.md#op_sv)|构造 `string_view` 、 `wstring_view` 、或，具体取决于将 `u16string_view` `u32string_view` 其追加到的字符串文本的类型。|

### <a name="classes"></a>类

|类|描述|
|-|-|
|[basic_string_view 类](../standard-library/basic-string-view-class.md)|一个类模板，它提供一个只读视图，并将其用作任意类似于字符的对象的序列。|
|[hash](string-view-hash.md)|为 string_view 生成哈希值的函数对象。|

## <a name="requirements"></a>要求

- **标头：**\<string_view>

- **命名空间:** std

- **编译器选项：** std： c + + 17 （或更高版本）

## <a name="see-also"></a>另请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)
