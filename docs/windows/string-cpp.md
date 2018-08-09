---
title: 字符串 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.string
dev_langs:
- C++
helpviewer_keywords:
- string attribute
ms.assetid: ddde900a-2e99-4fcd-86e8-57e1bdba7c93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 459f786863f7d10797008b87e276afb0c95e184a
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020081"
---
# <a name="string-c"></a>string (C++)
指示的一维**char**， **wchar_t**， `byte` （或等效） 必须作为字符串处理数组或指针，指向此类。  
  
## <a name="syntax"></a>语法  
  
```cpp  
[string]  
```  
  
## <a name="remarks"></a>备注  
 **字符串**c + + 属性具有相同的功能[字符串](http://msdn.microsoft.com/library/windows/desktop/aa367270)MIDL 特性。  
  
## <a name="example"></a>示例  
 下面的代码演示如何使用**字符串**接口上和 typedef:  
  
```cpp  
// cpp_attr_ref_string.cpp  
// compile with: /LD  
#include "unknwn.h"  
[module(name="ATLFIRELib")];  
[export, string] typedef char a[21];  
[dispinterface, restricted, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl  
{  
   [id(1)] HRESULT Method3([in, string] char *pC);  
};  
```  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|数组或指针，指向 array，接口参数，接口方法|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
 [数组特性](../windows/array-attributes.md)   
 [export](../windows/export.md)   