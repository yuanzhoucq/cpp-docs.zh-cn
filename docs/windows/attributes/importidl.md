---
title: importidl (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.importidl
helpviewer_keywords:
- importidl attribute
ms.assetid: 4b0a4b55-6c57-4e6e-bc7b-a12cc8063941
ms.openlocfilehash: 9db62d4f2a36b8cc0592c924b113077a758915c0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409429"
---
# <a name="importidl"></a>importidl

将指定的.idl 文件插入到生成的.idl 文件。

## <a name="syntax"></a>语法

```cpp
[ importidl(idl_file) ];
```

### <a name="parameters"></a>参数

*idl_file*<br/>
标识你想要将与你的应用程序将生成的.idl 文件合并的.idl 文件的名称。

## <a name="remarks"></a>备注

**Importidl** C++属性将放置在库块之外的部分 (在*idl_file*) 到您的程序生成的.idl 文件和库部分 (在*idl_file*)到程序的生成的.idl 文件的库的一部分。

您可能想要使用**importidl**，例如，如果你想要生成的.idl 文件中使用手工编码.idl 文件。

## <a name="example"></a>示例

```cpp
// cpp_attr_ref_importidl.cpp
// compile with: /LD
[module(name="MyLib")];
[importidl("import.idl")];
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|任何位置|
|**可重复**|否|
|**必需的特性**|None|
|**无效的特性**|None|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[编译器特性](compiler-attributes.md)<br/>
[独立特性](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importlib](importlib.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)