---
title: 自定义 （c + +） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.custom
dev_langs:
- C++
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7b37d87d5380b9d4dac69cee702654285461ead6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="custom-c"></a>custom (C++)
在类型库中定义的对象的元数据。  
  
## <a name="syntax"></a>语法  
  
```  
  
      [ custom(  
   uuid,   
   value  
) ];  
```  
  
#### <a name="parameters"></a>参数  
 *uuid*  
 唯一 ID。  
  
 *value*  
 一个值，可以将放入一个变体。  
  
## <a name="remarks"></a>备注  
 **自定义**c + + 特性会导致信息放入类型库。 你将需要一种工具，从类型库中读取自定义值。  
  
 **自定义**属性具有相同的功能[自定义](http://msdn.microsoft.com/library/windows/desktop/aa366766)MIDL 特性。  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|非 COM `interface`，**类**， `enum`s，`idl_module`方法、 接口成员、 接口参数`typedef`s，**联合**s， `struct`s|  
|**可重复**|是|  
|**必需的特性**|**组件类**（时在类上使用）|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
 [独立特性](../windows/stand-alone-attributes.md)   
 [Typedef、 Enum、 Union 和 Struct 特性](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Parameter 特性](../windows/parameter-attributes.md)   
 [方法特性](../windows/method-attributes.md)   
 [类特性](../windows/class-attributes.md)   
 [接口特性](../windows/interface-attributes.md)   
