---
title: 默认值 （c + + COM 属性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
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
ms.openlocfilehash: 5fb7f205ccdf78e1ef64e2ba2c132e3c2b6b6000
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790531"
---
# <a name="default-c"></a>default (C++)

指示组件类中定义的自定义接口或调度接口表示默认的可编程性接口。

## <a name="syntax"></a>语法

```cpp
[ default(interface1, interface2) ]
```

### <a name="parameters"></a>参数

*interface1*<br/>
默认接口，将可用于根据类（使用 **default** 属性定义）创建对象的脚本环境。

如果未指定默认接口，则第一个出现的非源接口用作默认接口。

*接口 2*<br/>
（可选）默认源接口。 您还必须指定此接口[源](source-cpp.md)属性。

如果未指定默认源接口，则第一个源接口用作默认接口。

## <a name="remarks"></a>备注

**默认**c + + 属性具有相同的功能[默认](/windows/desktop/Midl/default)MIDL 特性。 **默认**特性也用于[用例](case-cpp.md)属性。

## <a name="example"></a>示例

下面的代码演示如何**默认**组件类的定义中用于指定`ICustomDispatch`为默认可编程性接口：

```cpp
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

[   coclass, default(ICustomDispatch), source(IDual), uuid("9E66A294-4365-11D2-A997-00C04FA37DDB")  
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

[源](source-cpp.md)属性也有举例说明如何使用**默认**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**类**，**结构**，数据成员|
|**可重复**|否|
|**必需的特性**|**组件类**(当应用于**类**或**结构**)|
|**无效的特性**|无|

有关详细信息，请参阅[特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[coclass](coclass.md)  