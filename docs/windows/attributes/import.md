---
title: 导入C++ (COM 特性)
ms.date: 10/03/2018
f1_keywords:
- vc-attr.import
helpviewer_keywords:
- import attribute
ms.assetid: ebf07cae-39fb-4047-8b57-54af0a9a83de
ms.openlocfilehash: f9ed80bdcc04302c0dee85935f377c8e3dbfd37f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514619"
---
# <a name="import"></a>import

指定另一个 .idl、odl 或头文件, 该文件包含要从主 IDL 引用的定义。

## <a name="syntax"></a>语法

```cpp
[ import(
   idl_file
) ];
```

### <a name="parameters"></a>参数

*idl_file*<br/>
要导入到当前项目的类型库中的 .idl 文件的名称。

## <a name="remarks"></a>备注

**Import** C++ `import "docobj.idl"`特性导致语句放置在生成的 .idl 文件中的语句的下方。 `#import` **Import**特性与 "[导入](/windows/win32/Midl/import)MIDL" 特性具有相同的功能。

**Import**特性仅将指定的文件放入将由您的项目生成的 .idl 文件中;**import**特性不允许从项目的源代码中调用指定文件中的构造。  若要从项目中的源代码调用指定文件中的构造, 请使用[#import](../../preprocessor/hash-import-directive-cpp.md)和`embedded_idl`属性, 或者可以包含*idl_file*的 .h 文件 (如果存在 .h 文件)。

## <a name="example"></a>示例

下面的代码：

```cpp
// cpp_attr_ref_import.cpp
// compile with: /LD
[module(name="MyLib")];
[import(import.idl)];
```

在生成的 .idl 文件中生成以下代码:

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
|**适用于**|任何位置|
|**可重复**|No|
|**必需的特性**|无|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[独立特性](stand-alone-attributes.md)<br/>
[importidl](importidl.md)<br/>
[importlib](importlib.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)