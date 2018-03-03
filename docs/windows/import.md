---
title: "导入 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.import
dev_langs:
- C++
helpviewer_keywords:
- import attribute
ms.assetid: ebf07cae-39fb-4047-8b57-54af0a9a83de
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 011cabb37f388d4be6a9a69f685a7c711f0209a6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="import"></a>import
指定包含你想要从主 IDL 中引用的定义的另一个.idl、.odl 或标头文件。  
  
## <a name="syntax"></a>语法  
  
```  
  
      [ import(  
   idl_file  
) ];  
```  
  
#### <a name="parameters"></a>参数  
 `idl_file`  
 要导入当前项目的类型库的.idl 文件的名称。  
  
## <a name="remarks"></a>备注  
 **导入**c + + 特性将导致`#import`语句下面放置`import "docobj.idl"`生成的.idl 文件中的语句。 **导入**属性具有相同的功能[导入](http://msdn.microsoft.com/library/windows/desktop/aa367047)MIDL 特性。  
  
 **导入**属性仅将指定的文件放入将由你的项目; 生成的.idl 文件**导入**属性不允许您从源代码中指定的文件调用构造在你的项目。  若要从项目中的源代码中指定的文件调用构造，请使用[#import](../preprocessor/hash-import-directive-cpp.md)和`embedded_idl`属性也可以将的.h 文件`idl_file`，如果存在的.h 文件。  
  
## <a name="example"></a>示例  
 下面的代码：  
  
```  
// cpp_attr_ref_import.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[import(import.idl)];  
```  
  
 产生生成的.idl 文件中的以下代码：  
  
```  
import "docobj.idl";  
import "import.idl";  
  
[ uuid(EED3644C-8488-3ECD-BA97-147DB3CDB499), version(1.0) ]  
library MyLib {  
   importlib("stdole2.tlb");  
   importlib("olepro32.dll");  
...  
```  
  
## <a name="requirements"></a>惠?  
  
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
 [importidl](../windows/importidl.md)   
 [importlib](../windows/importlib.md)   
 [包括](../windows/include-cpp.md)   
 [includelib](../windows/includelib-cpp.md)   
