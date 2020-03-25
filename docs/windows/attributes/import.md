---
title: 导入C++ （COM 特性）
ms.date: 10/03/2018
f1_keywords:
- vc-attr.import
helpviewer_keywords:
- import attribute
ms.assetid: ebf07cae-39fb-4047-8b57-54af0a9a83de
ms.openlocfilehash: f2a0aa9a68c081e83a7a5278aa37a7fddac85416
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166831"
---
# <a name="import"></a>进口

指定另一个 .idl、odl 或头文件，该文件包含要从主 IDL 引用的定义。

## <a name="syntax"></a>语法

```cpp
[ import(
   idl_file
) ];
```

### <a name="parameters"></a>parameters

*idl_file*<br/>
要导入到当前项目的类型库中的 .idl 文件的名称。

## <a name="remarks"></a>备注

**Import** C++特性导致将 `#import` 语句放置在生成的 .idl 文件中的 `import "docobj.idl"` 语句的下方。 **Import**特性与 "[导入](/windows/win32/Midl/import)MIDL" 特性具有相同的功能。

**Import**特性仅将指定的文件放入将由您的项目生成的 .idl 文件中;**import**特性不允许从项目的源代码中调用指定文件中的构造。  若要从项目中的源代码调用指定文件中的构造，请使用[#import](../../preprocessor/hash-import-directive-cpp.md)和 `embedded_idl` 属性，或者，如果存在 .h 文件，则可以包括*idl_file*的 .h 文件。

## <a name="example"></a>示例

以下代码：

```cpp
// cpp_attr_ref_import.cpp
// compile with: /LD
[module(name="MyLib")];
[import(import.idl)];
```

在生成的 .idl 文件中生成以下代码：

```
import "docobj.idl";
import "import.idl";

[ uuid(EED3644C-8488-3ECD-BA97-147DB3CDB499), version(1.0) ]
library MyLib {
   importlib("stdole2.tlb");
   importlib("olepro32.dll");
...
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

## <a name="see-also"></a>另请参阅

[IDL 特性](idl-attributes.md)<br/>
[独立特性](stand-alone-attributes.md)<br/>
[importidl](importidl.md)<br/>
[importlib](importlib.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)
