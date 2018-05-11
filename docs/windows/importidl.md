---
title: importidl |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.importidl
dev_langs:
- C++
helpviewer_keywords:
- importidl attribute
ms.assetid: 4b0a4b55-6c57-4e6e-bc7b-a12cc8063941
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f5284c631813271f5682343c74cff693d1ea785e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="importidl"></a>importidl
将指定的.idl 文件插入到生成的.idl 文件中。  
  
## <a name="syntax"></a>语法  
  
```  
  
      [ importidl(  
   idl_file  
) ];  
```  
  
#### <a name="parameters"></a>参数  
 `idl_file`  
 标识你想要将与你的应用程序将生成的.idl 文件合并在.idl 文件的名称。  
  
## <a name="remarks"></a>备注  
 **Importidl** c + + 特性放置之外的库块的部分 (在`idl_file`) 到你的程序生成的.idl 文件和库部分 (在`idl_file`) 到你的程序的库部分生成的.idl 文件。  
  
 你可能想要使用**importidl**，例如，如果你想要使用生成的.idl 文件手工编码.idl 文件。  
  
## <a name="example"></a>示例  
  
```  
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
  
 有关详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [编译器特性](../windows/compiler-attributes.md)   
 [独立特性](../windows/stand-alone-attributes.md)   
 [导入](../windows/import.md)   
 [importlib](../windows/importlib.md)   
 [包括](../windows/include-cpp.md)   
 [includelib](../windows/includelib-cpp.md)   
