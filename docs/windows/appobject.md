---
title: "appobject |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.appobject
dev_langs: C++
helpviewer_keywords: appobject attribute
ms.assetid: 8ce30b73-e945-403e-a755-6bc78078a695
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 19462987cf4f9b5cc295766a694f01b8b4fac8ba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="appobject"></a>appobject
标识为应用程序对象，这些关联与完整.exe 应用程序，并指示是否在此全局提供的函数和属性组件类组件类[类型库](../mfc/automation-clients-using-type-libraries.md)。  
  
## <a name="syntax"></a>语法  
  
```  
  
[appobject]  
  
```  
  
## <a name="remarks"></a>备注  
 **Appobject** c + + 属性具有相同的功能[appobject](http://msdn.microsoft.com/library/windows/desktop/aa366726) MIDL 特性。  
  
## <a name="example"></a>示例  
 下面的代码演示前面要加特性块，其中包含一个简单的类定义**appobject**:  
  
```  
// cpp_attr_ref_appobject.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLib", uuid="f1ce17f0-a5df-4d26-95f6-0a122197ac5b")];  
  
[object, uuid="905de6db-7a12-45ab-9f8b-b39f5112f010"]  
__interface ICustom {};  
  
[coclass, appobject,uuid="00395340-745f-4b69-bd58-e2921452b9fc"]  
class A : public ICustom {  
   int i;  
};  
```  
  
## <a name="requirements"></a>惠?  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|**class**， `struct`|  
|**可重复**|否|  
|**必需的特性**|**coclass**|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
 [类特性](../windows/class-attributes.md)   
 [Typedef、Enum、Union 和 Struct 特性](../windows/typedef-enum-union-and-struct-attributes.md)   
