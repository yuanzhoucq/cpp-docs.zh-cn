---
title: 对象 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.object
dev_langs:
- C++
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2667c8ecb14e31388737366c4de6c527bdc40f9d
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40012747"
---
# <a name="object-c"></a>object (C++)
标识的自定义的接口。  
  
## <a name="syntax"></a>语法  
  
```cpp  
[object]  
```  
  
## <a name="remarks"></a>备注  
 前面的接口定义中，当**对象**c + + 属性导致将接口置于.idl 文件作为自定义的接口。  
  
 使用对象标记任何接口必须继承自`IUnknown`。 如果从任何基接口继承，则满足此条件`IUnknown`。 如果没有基接口继承自`IUnknown`，编译器将导致使用标记的接口**对象**为派生`IUnknown`。  
  
## <a name="example"></a>示例  
 请参阅[nonbrowsable](../windows/nonbrowsable.md)有关如何使用的示例**对象**。  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|**interface**|  
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