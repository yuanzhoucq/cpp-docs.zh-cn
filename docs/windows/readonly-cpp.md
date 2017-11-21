---
title: "readonly （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.readonly
dev_langs: C++
helpviewer_keywords: readonly attribute
ms.assetid: 1246cadd-5304-43a9-beea-51153d12704d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 52ee0c600cf12a9709072a8c1cb502dada70f708
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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
  
```  
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
|**可重复**|No|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
 [数据成员特性](../windows/data-member-attributes.md)   
