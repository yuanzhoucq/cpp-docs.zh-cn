---
title: 默认值 (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.default
helpviewer_keywords:
- default attribute
- attributes [C#], default attribute
- defaults, default attribute
ms.assetid: 0cdca716-1ba8-46d7-9399-167e55492870
ms.openlocfilehash: c6448b00fef50a7654816a2c39af2943db12d314
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148076"
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

*interface2*<br/>
（可选）默认源接口。 你还必须使用 [source](source-cpp.md) 属性指定此接口。

如果未指定默认源接口，则第一个源接口用作默认接口。

## <a name="remarks"></a>备注

**default** C++ 属性具有与 [default](/windows/desktop/Midl/default) MIDL 属性相同的功能。 **default** 属性还可以与 [case](case-cpp.md) 属性结合使用。

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

[source](source-cpp.md) 属性也有说明如何使用 **default**的示例。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**类**，**结构**，数据成员|
|**可重复**|否|
|**必需的特性**|**组件类**(当应用于**类**或**结构**)|
|**无效的特性**|None|

有关详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[coclass](coclass.md)