---
title: importidl （c + + COM 属性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.importidl
helpviewer_keywords:
- importidl attribute
ms.assetid: 4b0a4b55-6c57-4e6e-bc7b-a12cc8063941
ms.openlocfilehash: 8d0d891f74da8df2351b0a861fb7501e72f5e2de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587159"
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

**Importidl** c + + 属性会放置在库块之外的部分 (在*idl_file*) 到您的程序生成的.idl 文件和库部分 (在*idl_file*) 到库的应用程序的部分生成的.idl 文件。

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
|**必需的特性**|无|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[编译器特性](compiler-attributes.md)<br/>
[独立特性](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importlib](importlib.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)