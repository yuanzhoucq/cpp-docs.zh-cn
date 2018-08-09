---
title: includelib （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.includelib
dev_langs:
- C++
helpviewer_keywords:
- includelib attribute
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3d6f6a4dc4f23460b3661da4ed3775708cac9b6d
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016172"
---
# <a name="includelib-c"></a>includelib (C++)
导致要生成的.idl 文件中包含的.idl 或.h 文件。  
  
## <a name="syntax"></a>语法  
  
```cpp  
[ includelib(  
   name.idl  
) ];  
```  
  
### <a name="parameters"></a>参数  
 *name.idl*  
 要生成的.idl 文件的一部分的.idl 文件的名称。  
  
## <a name="remarks"></a>备注  
 **Includelib** c + + 属性会导致要包含在生成的.idl 文件中之后, 的.idl 或.h 文件`importlib`语句。  
  
## <a name="example"></a>示例  
 下面的代码是.cpp 文件中所示：  
  
```cpp  
// cpp_attr_ref_includelib.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[includelib("includelib.idl")];  
```  
  
## <a name="requirements"></a>要求  
  
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