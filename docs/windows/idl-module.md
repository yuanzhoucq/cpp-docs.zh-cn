---
title: idl_module |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.idl_module
dev_langs:
- C++
helpviewer_keywords:
- idl_module attribute
ms.assetid: 3578b337-e38a-4334-b747-15404c02dbc0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9fc3be9fb25b6593f4b69f846394544b7b7d756a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220460"
---
# <a name="idlmodule"></a>idl_module

.Dll 文件中指定的入口点。

## <a name="syntax"></a>语法

```cpp
[ idl_module (
   name=module_name,
   dllname=dll,
   uuid="uuid",
   helpstring="help text",
   helpstringcontext=helpcontextID,
   helpcontext=helpcontext,
   hidden,
   restricted
) ]
function declaration
```

### <a name="parameters"></a>参数

*name*  
用户定义的名称，会在.idl 文件中显示的代码块。

*dll 名称*（可选）  
包含导出的.dll 文件。

*uuid* （可选）  
唯一 ID。

*helpstring* （可选）  
用于描述类型库的字符串。

*helpstringcontext* （可选）  
帮助主题中的.hlp 或.chm 文件的 ID。

*helpcontext* （可选）  
该类型库的帮助 ID。

*隐藏*（可选）  
一个参数，阻止显示库。 请参阅[隐藏](/windows/desktop/Midl/hidden)MIDL 特性的详细信息。

*受限*（可选）  
不能随意调用库中的成员。 请参阅[受限](/windows/desktop/Midl/restricted)MIDL 特性的详细信息。

*函数声明*  
您将定义该函数。

## <a name="remarks"></a>备注

**Idl_module** c + + 属性可以在.dll 文件，这允许您从一个.dll 文件导入指定的入口点。

**Idl_module**属性具有类似于的功能[模块](/windows/desktop/Midl/module)MIDL 特性。

你可以从一个 COM 对象，可以通过将 DLL 入口点置于.idl 文件中的 library 块中导出的.dll 文件从导出的任何内容。

你必须使用**idl_module**中两个步骤。 首先，必须定义一个名称/DLL 对。 然后，使用**idl_module**若要指定的入口点，指定的名称和任何其他属性。

## <a name="example"></a>示例

下面的代码演示如何使用**idl_module**属性：

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
|**适用对象**|任何位置|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。

## <a name="see-also"></a>请参阅

[IDL 特性](../windows/idl-attributes.md)  
[独立特性](../windows/stand-alone-attributes.md)  
[entry](../windows/entry.md)  