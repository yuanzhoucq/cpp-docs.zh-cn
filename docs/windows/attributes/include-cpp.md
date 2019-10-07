---
title: include (C++ COM 特性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.include
helpviewer_keywords:
- include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
ms.openlocfilehash: ece88ebd7b5d9d81beb871427b58a72b2cf02022
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514549"
---
# <a name="include-c"></a>include (C++)

指定要包含在生成的 .idl 文件中的一个或多个标头文件。

## <a name="syntax"></a>语法

```cpp
[ include(header_file) ];
```

### <a name="parameters"></a>参数

*header_file*<br/>
要包含在生成的 .idl 文件中的文件的名称。

## <a name="remarks"></a>备注

**Include** C++ `import "docobj.idl"`特性导致语句放置在生成的 .idl 文件中的语句的下方。 `#include`

**Include** C++特性具有与[include](/windows/win32/Midl/include) MIDL 特性相同的功能。

## <a name="example"></a>示例

下面的代码演示如何使用**include**的示例。 在此示例中, 文件包含 .h, 只包含一个`#include`语句。

```cpp
// cpp_attr_ref_include.cpp
// compile with: /LD
[module(name="MyLib")];
[include(cpp_attr_ref_include.h)];
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|任何位置|
|**可重复**|No|
|**必需的特性**|无|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[独立特性](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[includelib](includelib-cpp.md)<br/>
[importlib](importlib.md)