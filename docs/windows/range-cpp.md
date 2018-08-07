---
title: 范围 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.range
dev_langs:
- C++
helpviewer_keywords:
- range attribute
ms.assetid: f352f79e-ecb3-4cdd-9cdd-8406ef473594
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d8c7ab6dcfa4a085facf835343404de3ed4998a3
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39603437"
---
# <a name="range-c"></a>range (C++)
指定参数或在运行时设置其值的字段的允许值的范围。  
  
## <a name="syntax"></a>语法  
  
```  
[ range(  
   low,   
   high  
) ]  
```  
  
#### <a name="parameters"></a>参数  
 *low*  
 范围下限值。  
  
 *high*  
 高范围值。  
  
## <a name="remarks"></a>备注  
 **范围**c + + 属性具有相同的功能[范围](http://msdn.microsoft.com/library/windows/desktop/aa367151)MIDL 特性。  
  
## <a name="example"></a>示例  
  
```cpp  
// cpp_attr_ref_range.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLib")];  
  
[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]  
__interface ICustom {  
   HRESULT Custom([in] long l, [out, retval] long *pLong);  
   HRESULT length_is1([in, range(0, 999)] long f, [in, length_is(f)] char array[10]);  
   HRESULT length_is2([in, range(-99, -1)] long f, [in, length_is("f"), size_is(10)] char *array);  
};  
```  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|接口方法，接口参数|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
 有关特性上下文的详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
 [方法特性](../windows/method-attributes.md)   
 [参数特性](../windows/parameter-attributes.md)   
 [数据成员特性](../windows/data-member-attributes.md)   