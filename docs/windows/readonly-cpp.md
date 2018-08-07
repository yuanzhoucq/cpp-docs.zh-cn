---
title: readonly （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.readonly
dev_langs:
- C++
helpviewer_keywords:
- readonly attribute
ms.assetid: 1246cadd-5304-43a9-beea-51153d12704d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4b4f4e6d7c3941b1e90e0c49d113afe02dfcd491
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39604419"
---
# <a name="readonly-c"></a>readonly (C++)
禁止分配给数据成员。  
  
## <a name="syntax"></a>语法  
  
```  
[readonly]  
```  
  
## <a name="remarks"></a>备注  
 **readonly** C++ 属性具有与 [readonly](http://msdn.microsoft.com/library/windows/desktop/aa367152) MIDL 属性相同的功能。  
  
 如果要禁止修改方法参数，则使用 [in](../windows/in-cpp.md) 属性。  
  
## <a name="example"></a>示例  
 下面的代码演示的 **readonly** 属性的用法：  
  
```cpp  
// cpp_attr_ref_readonly.cpp  
// compile with: /LD  
[idl_quote("midl_pragma warning(disable:2461)")];  
#include "unknwn.h"  
[module(name="ATLFIRELib")];  
  
[dispinterface, uuid(11111111-1111-1111-1111-111111111111)]  
__interface IFireTabCtrl  
{  
   [readonly, id(1)] int i();  
};  
```  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|接口方法|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
 [数据成员特性](../windows/data-member-attributes.md)   