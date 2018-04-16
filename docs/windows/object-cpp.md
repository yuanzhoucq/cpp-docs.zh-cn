---
title: "对象 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.object
dev_langs:
- C++
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5714d7c3bd029c7b1df636044ed1968f53600848
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="object-c"></a>object (C++)
标识的自定义的接口。  
  
## <a name="syntax"></a>语法  
  
```  
  
[object]  
  
```  
  
## <a name="remarks"></a>备注  
 前面的接口定义中，当**对象**c + + 特性将导致要放置在.idl 文件中为自定义接口的接口。  
  
 使用对象标记任何接口必须继承自**IUnknown**。 如果任何基接口继承自满足此条件**IUnknown**。 如果没有基接口继承自**IUnknown**，编译器将导致与标记的接口**对象**为派生自**IUnknown**。  
  
## <a name="example"></a>示例  
 请参阅[nonbrowsable](../windows/nonbrowsable.md)以举例说明如何使用**对象**。  
  
## <a name="requirements"></a>惠?  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|`interface`|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
 [接口特性](../windows/interface-attributes.md)   
 [双](../windows/dual.md)   
 [调度接口](../windows/dispinterface.md)   
 [自定义](../windows/custom-cpp.md)   
 [__interface](../cpp/interface.md)   
