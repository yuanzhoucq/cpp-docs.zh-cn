---
title: idl_module (C++ COM 特性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.idl_module
helpviewer_keywords:
- idl_module attribute
ms.assetid: 3578b337-e38a-4334-b747-15404c02dbc0
ms.openlocfilehash: 8838a833552ae7066dbcf17b4f676d6626c069f8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514671"
---
# <a name="idl_module"></a>idl_module

指定 .dll 文件中的入口点。

## <a name="syntax"></a>语法

```cpp
[ idl_module (name=module_name, dllname=dll, uuid="uuid", helpstring="help text", helpstringcontext=helpcontextID, helpcontext=helpcontext, hidden, restricted) ]
function declaration
```

### <a name="parameters"></a>参数

*名称*<br/>
将出现在 .idl 文件中的代码块的用户定义名称。

*dllname*<br/>
可有可无包含导出的 .dll 文件。

*uuid*<br/>
可有可无唯一 ID。

*helpstring*<br/>
可有可无用于描述类型库的字符串。

*helpstringcontext*<br/>
可有可无.Hlp 或 .chm 文件中的帮助主题的 ID。

*helpcontext*<br/>
可有可无此类型库的帮助 ID。

*hidden*<br/>
可有可无用于阻止显示库的参数。 更多详细信息，请参阅 [隐藏](/windows/win32/Midl/hidden) MIDL 特性。

*restricted*<br/>
可有可无不能随意调用库的成员。 更多详细信息，请参阅 [受限](/windows/win32/Midl/restricted) MIDL 特性。

*函数声明*<br/>
要定义的函数。

## <a name="remarks"></a>备注

**Idl_module** C++属性允许您在 .dll 文件中指定入口点, 以便您可以从 .dll 文件导入。

**Idl_module**属性具有与[module](/windows/win32/Midl/module) MIDL 属性类似的功能。

您可以通过将 DLL 入口点置于 .idl 文件的库块中, 从一个 COM 对象导出可以从 .dll 文件导出的任何内容。

必须在两个步骤中使用**idl_module** 。 首先, 必须定义名称/DLL 对。 然后, 当你使用**idl_module**来指定入口点时, 请指定名称和任何其他属性。

## <a name="example"></a>示例

下面的代码演示如何使用**idl_module**特性:

```cpp
// cpp_attr_ref_idl_module.cpp
// compile with: /LD
[idl_quote("midl_pragma warning(disable:2461)")];
[module(name="MyLibrary"), idl_module(name="MyLib", dllname="xxx.dll")];
[idl_module(name="MyLib"), entry(4), usesgetlasterror]
void FuncName(int i);
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
[entry](entry.md)