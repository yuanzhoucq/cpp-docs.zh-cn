---
title: 包括 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.include
dev_langs:
- C++
helpviewer_keywords:
- include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 617747a9eda77d8dc2ba21006b649daead9546d3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419316"
---
# <a name="include-c"></a>include (C++)

指定要包括在生成的.idl 文件中的一个或多个标头文件。

## <a name="syntax"></a>语法

```cpp
[ include(
   header_file
) ];
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

有关详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。

## <a name="see-also"></a>请参阅

[IDL 特性](../windows/idl-attributes.md)<br/>
[独立特性](../windows/stand-alone-attributes.md)<br/>
[import](../windows/import.md)<br/>
[importidl](../windows/importidl.md)<br/>
[includelib](../windows/includelib-cpp.md)<br/>
[importlib](../windows/importlib.md)  