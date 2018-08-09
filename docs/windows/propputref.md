---
title: propputref |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.propputref
dev_langs:
- C++
helpviewer_keywords:
- propputref attribute
ms.assetid: 9b0aed74-fdc7-4e59-9117-949bea4f86dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d72fa9523b850e5c7d76b587c37b181f21df25c0
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013975"
---
# <a name="propputref"></a>propputref
指定使用引用而不是值的属性设置函数。  
  
## <a name="syntax"></a>语法  
  
```cpp  
[propputref]  
```  
  
## <a name="remarks"></a>备注  
 **Propputref** c + + 属性具有相同的功能[propputref](http://msdn.microsoft.com/library/windows/desktop/aa367147) MIDL 特性。  
  
## <a name="example"></a>示例  
 有关示例，请参阅[可绑定](../windows/bindable.md)的示例使用**propputref**。  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|方法|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|`propget`, `propput`|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
 [方法特性](../windows/method-attributes.md)   
 [propget](../windows/propget.md)   
 [propput](../windows/propput.md)   