---
title: "idl_module | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.idl_module"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "idl_module attribute"
ms.assetid: 3578b337-e38a-4334-b747-15404c02dbc0
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# idl_module
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 .dll 文件指定入口点。  
  
## 语法  
  
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
  
#### 参数  
 **名称**  
 一个用户定义的名称将显示在 .idl 文件中的代码块。  
  
 **dllname** \(可选\)  
 包含导出的 .dll 文件。  
  
 `uuid`（可选）  
 唯一 ID。  
  
 **helpstring** \(可选\)  
 用于的字符串\) 描述类型库。  
  
 **helpstringcontext** \(可选\)  
 帮助主题的 ID。 .hlp 或 .chm 文件的。  
  
 **helpcontext** \(可选\)  
 此类型的库中用来帮助 ID。  
  
 **隐藏** \(可选\)  
 防止库中显示的参数。  请参见 [隐藏](http://msdn.microsoft.com/library/windows/desktop/aa366861) MIDL 属性有关更多信息。  
  
 ***限制***  \(可选\)  
 库的成员不能随机调用。  请参见 [限制](http://msdn.microsoft.com/library/windows/desktop/aa367157) MIDL 属性有关更多信息。  
  
 *函数声明*  
 您将定义的函数。  
  
## 备注  
 `idl_module` C\+\+ 特性在 .dll 文件允许您指定入口点，允许从 .dll 文件导入。  
  
 **idl\_module** 属性具有功能类似于 [模块](http://msdn.microsoft.com/library/windows/desktop/aa367099) MIDL 属性。  
  
 可以从可以从 .dll 文件导出通过将 DLL 在库中入口点块 .idl 文件中的 COM 对象导出任何操作。  
  
 在两个步骤所需使用 `idl_module` 。  首先，必须定义 name\/DLL 对。  然后，那么，当您使用 `idl_module` 指定入口点时，指定名称和附加的属性。  
  
## 示例  
 下面的代码演示如何使用 `idl_module` 属性:  
  
```  
// cpp_attr_ref_idl_module.cpp  
// compile with: /LD  
[idl_quote("midl_pragma warning(disable:2461)")];  
[module(name="MyLibrary"), idl_module(name="MyLib", dllname="xxx.dll")];  
[idl_module(name="MyLib"), entry(4), usesgetlasterror]  
void FuncName(int i);  
```  
  
## 要求  
  
### 属性上下文  
  
|||  
|-|-|  
|**适用对象**|任何位置|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关更多信息，请参见 [属性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Stand\-Alone Attributes](../windows/stand-alone-attributes.md)   
 [entry](../windows/entry.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)