---
title: "uuid （c + + 特性） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.uuid
dev_langs:
- C++
helpviewer_keywords:
- uuid attribute
ms.assetid: 90562a94-5e28-451b-a4b0-cadda7f66efe
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ba35dc89ae2567a499d4623f0c74293d2dbdcca2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="uuid-c-attributes"></a>uuid（C++ 特性）
指定为类或接口的唯一 ID。  
  
## <a name="syntax"></a>语法  
  
```  
  
      [ uuid(  
   "uuid"  
) ]  
```  
  
#### <a name="parameters"></a>参数  
 *uuid*  
 128 位的唯一标识符。  
  
## <a name="remarks"></a>备注  
 如果未指定的接口或类定义`uuid`c + + 属性，则 Visual c + + 编译器将提供一个。 当指定`uuid`，必须包括引号。  
  
 如果不指定`uuid`，则编译器将在一台计算机上的不同的属性项目中生成的 GUID 相同的接口或具有相同名称的类。  
  
 你可以使用 Uuidgen.exe 或 Guidgen.exe 生成你自己唯一的 Id。 (若要运行这些工具之一，请单击**启动**单击**运行**菜单上。 然后输入所需的工具的名称。）  
  
 也不使用 ATL 项目中使用时，指定`uuid`属性等同于指定[uuid](../cpp/uuid-cpp.md) __declspec 修饰符。 若要检索`uuid`的类，可以使用[__uuidof](../cpp/uuidof-operator.md)  
  
## <a name="example"></a>示例  
 请参阅[可绑定](../windows/bindable.md)更大的示例的示例使用`uuid`。  
  
## <a name="requirements"></a>惠?  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|**类**， `struct`， `interface`，**联合**，`enum`|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
 [接口特性](../windows/interface-attributes.md)   
 [类特性](../windows/class-attributes.md)   
 [Typedef、 Enum、 Union 和 Struct 特性](../windows/typedef-enum-union-and-struct-attributes.md)   
 [uuid](http://msdn.microsoft.com/library/windows/desktop/aa367302)   
