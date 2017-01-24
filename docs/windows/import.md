---
title: "import | Microsoft Docs"
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
  - "vc-attr.import"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "import attribute"
ms.assetid: ebf07cae-39fb-4047-8b57-54af0a9a83de
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# import
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定包含要从主 IDL 特性引用定义的另一个 .idl、 .odl 或头文件。  
  
## 语法  
  
```  
  
      [ import(  
   idl_file  
) ];  
```  
  
#### 参数  
 `idl_file`  
 要 .idl 文件的名称导入到当前项目的类型库。  
  
## 备注  
 **导入** C\+\+ 特性在生成的 .idl 文件错误引起一个 `#import` 语句放置在 `import "docobj.idl"` 语句下面。  **导入** 属性具有与 [导入](http://msdn.microsoft.com/library/windows/desktop/aa367047) MIDL 属性相同。  
  
 **导入** 属性只放置已指定的文件添加到将由项目生成的 .idl 文件; **导入** 属性不允许对指定文件所构造从某个项目的源代码。  ，如果 .h 文件，若要调用中指定的文件构造从在项目的源代码，使用 [\#import](../preprocessor/hash-import-directive-cpp.md) 和 `embedded_idl` 属性或您可以将 `idl_file`的 .h 文件。  
  
## 示例  
 下面的代码:  
  
```  
// cpp_attr_ref_import.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[import(import.idl)];  
```  
  
 导致在生成的 .idl 文件的以下代码:  
  
```  
import "docobj.idl";  
import "import.idl";  
  
[ uuid(EED3644C-8488-3ECD-BA97-147DB3CDB499), version(1.0) ]  
library MyLib {  
   importlib("stdole2.tlb");  
   importlib("olepro32.dll");  
...  
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
 [importidl](../windows/importidl.md)   
 [importlib](../windows/importlib.md)   
 [include](../windows/include-cpp.md)   
 [includelib](../windows/includelib-cpp.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)