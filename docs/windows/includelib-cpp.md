---
title: "includelib （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.includelib
dev_langs: C++
helpviewer_keywords: includelib attribute
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: df6c38889db24cc1b4f28ce0bfe4cf96eb6b03a2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="includelib-c"></a>includelib (C++)
导致要包含在生成的.idl 文件的.idl 或.h 文件。  
  
## <a name="syntax"></a>语法  
  
```  
  
      [ includelib(  
   name.idl  
) ];  
```  
  
#### <a name="parameters"></a>参数  
 *name.idl*  
 要生成的.idl 文件的一部分包括在.idl 文件的名称。  
  
## <a name="remarks"></a>备注  
 `includelib` C + + 特性将导致要包含在生成的.idl 文件中之后, 的.idl 或.h 文件`importlib`语句。  
  
## <a name="example"></a>示例  
 下面的代码是在.cpp 文件中所示：  
  
```  
// cpp_attr_ref_includelib.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[includelib("includelib.idl")];  
```  
  
## <a name="requirements"></a>惠?  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|任何位置|  
|**可重复**|是|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
 [独立特性](../windows/stand-alone-attributes.md)   
 [导入](../windows/import.md)   
 [importidl](../windows/importidl.md)   
 [包括](../windows/include-cpp.md)   
 [importlib](../windows/importlib.md)   
