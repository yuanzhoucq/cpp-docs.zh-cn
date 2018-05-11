---
title: 默认值 （c + +） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.default
dev_langs:
- C++
helpviewer_keywords:
- default attribute
- attributes [C#], default attribute
- defaults, default attribute
ms.assetid: 0cdca716-1ba8-46d7-9399-167e55492870
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bb701b91fc1e076dcf4e6540bf8bcaf6141ec6c6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="default-c"></a>default (C++)
指示组件类中定义的自定义接口或调度接口表示默认的可编程性接口。  
  
## <a name="syntax"></a>语法  
  
```  
  
      [ default(  
   interface1,  
   interface2  
) ]  
```  
  
#### <a name="parameters"></a>参数  
 *interface1*  
 默认接口，将可用于根据类（使用 **default** 属性定义）创建对象的脚本环境。  
  
 如果未指定默认接口，则第一个出现的非源接口用作默认接口。  
  
 *interface2*（可选）  
 默认源接口。 你还必须使用 [source](../windows/source-cpp.md) 属性指定此接口。  
  
 如果未指定默认源接口，则第一个源接口用作默认接口。  
  
## <a name="remarks"></a>备注  
 **default** C++ 属性具有与 [default](http://msdn.microsoft.com/library/windows/desktop/aa366787) MIDL 属性相同的功能。 **default** 属性还可以与 [case](../windows/case-cpp.md) 属性结合使用。  
  
## <a name="example"></a>示例  
 以下代码演示如何在组件类的定义中使用 **default** 来将 **ICustomDispatch** 指定为默认可编程性接口：  
  
```  
// cpp_attr_ref_default.cpp  
// compile with: /LD  
#include "windows.h"  
[module(name="MyLibrary")];  
  
[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]  
__interface ICustom {  
   HRESULT Custom([in] long l, [out, retval] long *pLong);  
};  
  
[dual, uuid("9E66A291-4365-11D2-A997-00C04FA37DDB")]   
__interface IDual {  
   HRESULT Dual([in] long l, [out, retval] long *pLong);  
};  
  
[object, uuid("9E66A293-4365-11D2-A997-00C04FA37DDB")]  
__interface ICustomDispatch : public IDispatch {  
   HRESULT Dispatch([in] long l, [out, retval] long *pLong);  
};  
  
[   coclass,  
   default(ICustomDispatch),   
   source(IDual),  
   uuid("9E66A294-4365-11D2-A997-00C04FA37DDB")  
]  
class CClass : public ICustom, public IDual, public ICustomDispatch {  
   HRESULT Custom(long l, long *pLong) { return(S_OK); }  
   HRESULT Dual(long l, long *pLong) { return(S_OK); }  
   HRESULT Dispatch(long l, long *pLong) { return(S_OK); }  
};  
  
int main() {  
#if 0 // Can't instantiate without implementations of IUnknown/IDispatch  
   CClass *pClass = new CClass;  
  
   long llong;  
  
   pClass->custom(1, &llong);  
   pClass->dual(1, &llong);  
   pClass->dispinterface(1, &llong);  
   pClass->dispatch(1, &llong);  
  
   delete pClass;  
#endif  
   return(0);  
}  
```  
  
 [source](../windows/source-cpp.md) 属性也有说明如何使用 **default**的示例。  
  
## <a name="requirements"></a>要求  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|**class**、 `struct`、数据成员|  
|**可重复**|否|  
|**必需的特性**|**coclass** （应用于 **class** 或 `struct`时）|  
|**无效的特性**|无|  
  
 有关详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
 [IDL 特性](../windows/idl-attributes.md)   
 [类特性](../windows/class-attributes.md)   
 [coclass](../windows/coclass.md)   
