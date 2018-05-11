---
title: cpp_quote |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.cpp_quote
dev_langs:
- C++
helpviewer_keywords:
- cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 38ecabcde55f49687abf7caff66fb2c316fab0fe
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="cppquote"></a>cpp_quote
发出指定的字符串，而无需引号字符，到生成的.idl 文件。  
  
## <a name="syntax"></a>语法  
  
```  
  
      [ cpp_quote(  
   "statement"  
) ];  
```  
  
#### <a name="parameters"></a>参数  
 statement  
 C 指令中。  
  
## <a name="remarks"></a>备注  
 **Cpp_quote** c + + 特性非常有用，如果你想要将预处理器指令放在.idl 文件。  
  
 你还可以使用**cpp_quote**并生成一个.h 文件作为 MIDL 编译的一部分。 例如，如果你有使用 c + + IDL 特性，但不能使用此文件执行某些任务的 c + + 头文件，然后你可以其进行编译以创建 MIDL 生成的.h 文件，你应该能够使用。  
  
 **Cpp_quote**属性具有相同的功能[cpp_quote](http://msdn.microsoft.com/library/windows/desktop/aa366765) MIDL 特性。  
  
## <a name="example"></a>示例  
 请参阅示例[双重](../windows/dual.md)有关用法示例如何使用**cpp_quote**。  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|任何位置|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
 [独立特性](../windows/stand-alone-attributes.md)   
