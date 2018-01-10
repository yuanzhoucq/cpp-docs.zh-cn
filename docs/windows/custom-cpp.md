---
title: "自定义 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.custom
dev_langs: C++
helpviewer_keywords: custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e55fd4ad47470a86a0a3d61cc847c20fb21768e8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
  
 *值*  
 一个值，可以将放入一个变体。  
  
## <a name="remarks"></a>备注  
 **自定义**c + + 特性会导致信息放入类型库。 你将需要一种工具，从类型库中读取自定义值。  
  
 **自定义**属性具有相同的功能[自定义](http://msdn.microsoft.com/library/windows/desktop/aa366766)MIDL 特性。  
  
## <a name="requirements"></a>惠?  
  
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
