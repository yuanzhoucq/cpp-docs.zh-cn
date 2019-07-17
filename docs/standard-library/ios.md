---
title: '&lt;ios&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ios>
- ios/std::<ios>
helpviewer_keywords:
- ios header
ms.assetid: d3d4c161-2f37-4f04-93cc-0a2a89984a9c
ms.openlocfilehash: 013888a1ae11042645ef48c4fae15cbe6c2d939f
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245238"
---
# <a name="ltiosgt"></a>&lt;ios&gt;

定义作为 iostreams 操作的基础的多种类型和函数。 此标头通常包含在另一 iostream 标头中；很少会直接包含它。

## <a name="requirements"></a>要求

**标头**: \<ios >

**命名空间：** std

> [!NOTE]
> \<Ios > 库使用`#include <iosfwd>`语句。

## <a name="remarks"></a>备注

一大组函数为操控器。 在 \<ios> 中声明的操控器可更改存储在其 [ios_base](../standard-library/ios-base-class.md) 类的自变量对象中的值。 其他操控器对由对象（其类型派生自此类）控制的流执行操作，如其中一个模板类 [basic_istream](../standard-library/basic-istream-class.md) 或 [basic_ostream](../standard-library/basic-ostream-class.md) 的专用化。 例如， [noskipws](../standard-library/ios-functions.md#noskipws)(**str**) 清除格式标志`ios_base::skipws`对象中`str`，它可以是以下类型之一。

还可以通过将操控器插入到输出流中或从输入流提取操控器对其进行调用，原因是为派生自 `ios_base` 的类提供了专门的插入和提取操作。 例如:

```cpp
istr>> noskipws;
```

调用 [noskipws](../standard-library/ios-functions.md#noskipws)(**istr**)。

## <a name="members"></a>成员

### <a name="typedefs"></a>Typedef

|||
|-|-|
|[ios](../standard-library/ios-typedefs.md#ios)|支持旧 iostream 库中的 ios 类。|
|[streamoff](../standard-library/ios-typedefs.md#streamoff)|支持内部操作。|
|[streampos](../standard-library/ios-typedefs.md#streampos)|保留缓冲区指针或文件指针的当前位置。|
|[streamsize](../standard-library/ios-typedefs.md#streamsize)|指定流的大小。|
|[wios](../standard-library/ios-typedefs.md#wios)|支持旧 iostream 库中的 wios 类。|
|[wstreampos](../standard-library/ios-typedefs.md#wstreampos)|保留缓冲区指针或文件指针的当前位置。|

### <a name="manipulators"></a>操控器

|||
|-|-|
|[boolalpha](../standard-library/ios-functions.md#boolalpha)|指定类型为 [bool](../cpp/bool-cpp.md) 的变量在流中显示为 **true** 或 **false**。|
|[dec](../standard-library/ios-functions.md#dec)|指定以十进制计数法形式显示整数变量。|
|[defaultfloat](../standard-library/ios-functions.md#ios_defaultfloat)|配置 `ios_base` 对象的标记以使用浮点值的默认显示格式。|
|[fixed](../standard-library/ios-functions.md#fixed)|指定浮点数以自动设置小数点表示法显示。|
|[hex](../standard-library/ios-functions.md#hex)|指定以十六进制计数法形式显示整数变量。|
|[hexfloat](../standard-library/ios-functions.md#hexfloat)|
|[internal](../standard-library/ios-functions.md#internal)|导致数字的符号左对齐，数字右对齐。|
|[left](../standard-library/ios-functions.md#left)|导致宽度比输出宽度短的文本在流刷新过程中显示时带有左边距。|
|[noboolalpha](../standard-library/ios-functions.md#noboolalpha)|指定类型为 [bool](../cpp/bool-cpp.md) 的变量在流中显示为 1 或 0。|
|[noshowbase](../standard-library/ios-functions.md#noshowbase)|关闭显示数字所采用的进制的指示。|
|[noshowpoint](../standard-library/ios-functions.md#noshowpoint)|仅显示浮点数（其小数部分为零）的整数部分。|
|[noshowpos](../standard-library/ios-functions.md#noshowpos)|导致正数不显式带有符号。|
|[noskipws](../standard-library/ios-functions.md#noskipws)|导致输入流读取空格。|
|[nounitbuf](../standard-library/ios-functions.md#nounitbuf)|导致缓冲区已满时缓冲和处理输出。|
|[nouppercase](../standard-library/ios-functions.md#nouppercase)|指定十六进制数字和科学计数法形式的指数以小写形式显示。|
|[oct](../standard-library/ios-functions.md#oct)|指定以八进制计数法形式显示整数变量。|
|[right](../standard-library/ios-functions.md#right)|导致宽度比输出宽度短的文本在流刷新过程中显示时带有右边距。|
|[scientific](../standard-library/ios-functions.md#scientific)|导致使用科学表示法显示浮点数。|
|[showbase](../standard-library/ios-functions.md#showbase)|指示显示数字所采用的进制。|
|[showpoint](../standard-library/ios-functions.md#showpoint)|显示浮点数的整数部分和小数点右侧的数字，即使小数部分为零。|
|[showpos](../standard-library/ios-functions.md#showpos)|导致正数显式带有符号。|
|[skipws](../standard-library/ios-functions.md#skipws)|导致输入流不读取空格。|
|[unitbuf](../standard-library/ios-functions.md#unitbuf)|导致在缓冲区未满时处理输出。|
|[uppercase](../standard-library/ios-functions.md#uppercase)|指定十六进制数字和科学计数法形式的指数以大写形式显示。|

### <a name="error-reporting"></a>错误报告

|||
|-|-|
|[io_errc](../standard-library/ios-functions.md#io_errc)||
|[is_error_code_enum](../standard-library/ios-functions.md#is_error_code_enum)||
|[iostream_category](../standard-library/ios-functions.md#iostream_category)||
|[make_error_code](../standard-library/ios-functions.md#make_error_code)||
|[make_error_condition](../standard-library/ios-functions.md#make_error_condition)||

### <a name="classes"></a>类

|||
|-|-|
|[basic_ios](../standard-library/basic-ios-class.md)|此模板类描述了依赖于模板参数的输入流（属于模板类 [basic_istream](../standard-library/basic-istream-class.md)）和输出流（属于模板类 [basic_ostream](../standard-library/basic-ostream-class.md)）通用的存储和成员函数。|
|[fpos](../standard-library/fpos-class.md)|此模板类描述了一个对象，该对象可以存储还原任何流内的任意文件位置指示器所需的全部信息。|
|[ios_base](../standard-library/ios-base-class.md)|此类描述了不依赖模板参数的输入和输出流通用的存储和成员函数。|

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 编程](../standard-library/iostream-programming.md)<br/>
[iostreams 约定](../standard-library/iostreams-conventions.md)<br/>
