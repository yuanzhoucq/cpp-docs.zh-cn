---
title: retval |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.retval
dev_langs:
- C++
helpviewer_keywords:
- retval attribute
ms.assetid: bfa16f08-157d-4eea-afde-1232c54b8501
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1c0bf7ecd989b51a17c853c6d2986db204c3ce34
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33888716"
---
# <a name="retval"></a>retval
指定参数，用于接收成员的返回值。  
  
## <a name="syntax"></a>语法  
  
```  
  
[retval]  
  
```  
  
## <a name="remarks"></a>备注  
 **Retval** c + + 属性具有相同的功能[retval](http://msdn.microsoft.com/library/windows/desktop/aa367158) MIDL 特性。  
  
 **retval**必须出现在函数的声明中的最后一个参数。  
  
## <a name="example"></a>示例  
 请参阅示例[可绑定](../windows/bindable.md)的示例使用**retval**。  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|接口参数，接口方法|  
|**可重复**|否|  
|**必需的特性**|**out**|  
|**无效的特性**|**in**|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
 [Parameter 特性](../windows/parameter-attributes.md)   
 [方法特性](../windows/method-attributes.md)   
