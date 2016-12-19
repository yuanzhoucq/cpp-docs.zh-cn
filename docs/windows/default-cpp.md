---
title: "default (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.default"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "default 特性"
  - "属性 [C#], 默认属性"
  - "默认值, 默认属性"
ms.assetid: 0cdca716-1ba8-46d7-9399-167e55492870
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# default (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示组件类中定义的自定义接口或调度接口表示默认的可编程性接口。  
  
## 语法  
  
```  
  
[ default(  
interface1  
,  
   interface2  
) ]  
  
```  
  
#### 参数  
 *interface1*  
 默认接口，将可用于根据类（使用 **default** 属性定义）创建对象的脚本环境。  
  
 如果未指定默认接口，则第一个出现的非源接口用作默认接口。  
  
 *interface2*（可选）  
 默认源接口。 你还必须使用 [source](../windows/source-cpp.md) 属性指定此接口。  
  
 如果未指定默认源接口，则第一个源接口用作默认接口。  
  
## 备注  
 **default** C\+\+ 属性具有与 [default](http://msdn.microsoft.com/library/windows/desktop/aa366787) MIDL 属性相同的功能。**default** 属性还可以与 [case](../windows/case-cpp.md) 属性结合使用。  
  
## 示例  
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
  
 [source](../windows/source-cpp.md) 属性也有说明如何使用 **default** 的示例。  
  
## 要求  
  
### 特性上下文  
  
|||  
|-|-|  
|**适用对象**|**class**、`struct`、数据成员|  
|**可重复**|No|  
|**必需的特性**|**coclass**（应用于**class** 或 `struct` 时）|  
|**无效的特性**|无|  
  
 有关详细信息，请参见[特性上下文](../windows/attribute-contexts.md)。  
  
## 请参阅  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Class Attributes](../windows/class-attributes.md)   
 [coclass](../windows/coclass.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-cn/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)