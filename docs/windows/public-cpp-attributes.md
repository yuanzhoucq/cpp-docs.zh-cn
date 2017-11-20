---
title: "公共 （c + + 特性） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.public
dev_langs: C++
helpviewer_keywords: public attribute
ms.assetid: c42e1fd5-6cb1-48fe-8a03-95f2a2e0137c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c464f2fe2261018f2f18282b3cf3c2a62f31fde4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="public-c-attributes"></a>public（C++ 特性）
可确保即使它未从引用.idl 文件中，typedef 将转到类型库。  
  
## <a name="syntax"></a>语法  
  
```  
  
[public]  
  
```  
  
## <a name="remarks"></a>备注  
 **公共**c + + 属性具有相同的功能[公共](http://msdn.microsoft.com/library/windows/desktop/aa367150)MIDL 特性。  
  
## <a name="example"></a>示例  
 下面的代码演示如何使用**公共**属性：  
  
```  
// cpp_attr_ref_public.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="ATLFIRELib")];  
[export, public] typedef long MEMBERID;  
  
[dispinterface, uuid(99999999-9999-9999-9999-000000000000)]  
__interface IFireTabCtrl : IDispatch  
{  
   [id(2)] long procedure ([in, optional] VARIANT i);  
};  
```  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|`typedef`|  
|**可重复**|No|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>另请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
 [Typedef、Enum、Union 和 Struct 特性](../windows/typedef-enum-union-and-struct-attributes.md)   
