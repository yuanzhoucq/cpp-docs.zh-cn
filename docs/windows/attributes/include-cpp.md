---
title: 包括 （c + + COM 属性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.include
helpviewer_keywords:
- include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
ms.openlocfilehash: 6fb385877285602c1eb6649d11e16558d7fb07ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544750"
---
# <a name="include-c"></a>include (C++)

指定要包括在生成的.idl 文件中的一个或多个标头文件。

## <a name="syntax"></a>语法

```cpp
[ include(header_file) ];
```

### <a name="parameters"></a>参数

*header_file*<br/>
在生成的.idl 文件中包含所需的文件的名称。

## <a name="remarks"></a>备注

**包括**c + + 属性会导致`#include`语句下面放置`import "docobj.idl"`语句生成的.idl 文件中。

**包括**c + + 属性具有相同的功能[包括](/windows/desktop/Midl/include)MIDL 特性。

## <a name="example"></a>示例

下面的代码演示如何使用的示例**包括**。 对于此示例中，文件 include.h 仅包含`#include`语句。

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
|**适用对象**|任何位置|
|**可重复**|否|
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