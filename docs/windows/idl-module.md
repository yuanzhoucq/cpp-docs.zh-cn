---
title: idl_module |Microsoft 文档
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
ms.openlocfilehash: 11547a3fb1bd46a1e2edb8ce9dd0a6547464f796
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882519"
---
# <a name="idlmodule"></a>idl_module
指定的.dll 文件中的入口点。  
  
## <a name="syntax"></a>语法  
  
```  
  
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
  
#### <a name="parameters"></a>参数  
 **name**  
 用户定义的名称，将显示在.idl 文件的代码块。  
  
 **dll 名称**（可选）  
 包含导出的.dll 文件。  
  
 `uuid`（可选）  
 唯一 ID。  
  
 **helpstring** （可选）  
 用于描述类型库的字符字符串。  
  
 **helpstringcontext** （可选）  
 帮助主题中的.hlp 或.chm 文件的 ID。  
  
 **helpcontext** （可选）  
 该类型库的帮助 ID。  
  
 **隐藏** （可选）  
 一个参数，防止库显示。 更多详细信息，请参阅 [隐藏](http://msdn.microsoft.com/library/windows/desktop/aa366861) MIDL 特性。  
  
 ***受限***（可选）  
 不能任意调用的库的成员。 更多详细信息，请参阅 [受限](http://msdn.microsoft.com/library/windows/desktop/aa367157) MIDL 特性。  
  
 *函数声明*  
 你将定义函数。  
  
## <a name="remarks"></a>备注  
 `idl_module` C + + 属性允许您在.dll 文件中，可用于从.dll 文件导入指定的入口点。  
  
 **Idl_module**属性具有类似于功能[模块](http://msdn.microsoft.com/library/windows/desktop/aa367099)MIDL 特性。  
  
 你可以从一个 COM 对象，你可以从导出的.dll 文件通过将 DLL 入口点放在.idl 文件的库块中导出任何内容。  
  
 你必须使用`idl_module`中两个步骤。 首先，必须定义一个名称/DLL 对。 然后，使用`idl_module`若要指定的入口点，指定的名称和任何其他属性。  
  
## <a name="example"></a>示例  
 下面的代码演示如何使用`idl_module`属性：  
  
```  
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
