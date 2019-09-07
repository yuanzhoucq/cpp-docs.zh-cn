---
title: ATL 集合类
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- collection classes
ms.assetid: eff95de6-78ef-4212-9d7d-1dacbdd4cc58
ms.openlocfilehash: 09c0a64ff34a86c5581fe552ce2dbf0d12ea8e96
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739527"
---
# <a name="collection-classes"></a>集合类

以下类提供对数组、列表、映射以及用于帮助进行比较和元素访问的特性方法的支持。

- [CAtlArray](../atl/reference/catlarray-class.md)此类实现数组对象。

- [CAtlList](../atl/reference/catllist-class.md)此类提供用于创建和管理列表对象的方法。

- [CAtlMap](../atl/reference/catlmap-class.md)此类提供用于创建和管理地图对象的方法。

- [CAutoPtrArray](../atl/reference/cautoptrarray-class.md)此类提供在构造智能指针数组时有用的方法。

- [CAutoPtrElementTraits](../atl/reference/cautoptrelementtraits-class.md)此类提供在创建智能指针集合时有用的方法、静态函数和 typedef。

- [CAutoPtrList](../atl/reference/cautoptrlist-class.md)此类提供在构造智能指针列表时有用的方法。

- [CAutoVectorPtrElementTraits](../atl/reference/cautovectorptrelementtraits-class.md)使用向量 new 和 delete 运算符创建智能指针集合时，此类提供的方法、静态函数和 typedef 非常有用。

- [CComQIPtrElementTraits](../atl/reference/ccomqiptrelementtraits-class.md)此类提供方法、静态函数和 typedef 在创建 COM 接口指针的集合时非常有用。

- [CComSafeArray](../atl/reference/ccomsafearray-class.md)此类是[SAFEARRAY 数据类型](/windows/win32/api/oaidl/ns-oaidl-safearray)结构的包装器。

- [CComSafeArrayBound](../atl/reference/ccomsafearraybound-class.md)此类是[SAFEARRAYBOUND](/windows/win32/api/oaidl/ns-oaidl-safearraybound)结构的包装器。

- [CComUnkArray](../atl/reference/ccomunkarray-class.md)此类存储**IUnknown**指针，旨在用作[IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)模板类的参数。

- [CDefaultCharTraits](../atl/reference/cdefaultchartraits-class.md)此类提供两个用于在大写和小写之间转换字符的静态函数。

- [CDefaultCompareTraits](../atl/reference/cdefaultcomparetraits-class.md)此类提供默认元素比较函数。

- [CDefaultElementTraits](../atl/reference/cdefaultelementtraits-class.md)此类提供集合类的默认方法和函数。

- [CDefaultHashTraits](../atl/reference/cdefaulthashtraits-class.md)此类提供用于计算哈希值的静态函数。

- [CElementTraits](../atl/reference/celementtraits-class.md)集合类使用此类为移动、复制、比较和哈希操作提供方法和函数。

- [CElementTraitsBase](../atl/reference/celementtraitsbase-class.md)此类提供集合类的默认复制和移动方法。

- [CHeapPtrElementTraits](../atl/reference/cheapptrelementtraits-class.md)此类提供方法、静态函数和 typedef 在创建堆指针的集合时非常有用。

- [CHeapPtrList](../atl/reference/cheapptrlist-class.md)此类提供在构造堆指针列表时有用的方法。

- [CInterfaceArray](../atl/reference/cinterfacearray-class.md)此类提供在构造 COM 接口指针数组时有用的方法。

- [CInterfaceList](../atl/reference/cinterfacelist-class.md)此类提供的方法在构造 COM 接口指针的列表时很有用。

- [CPrimitiveElementTraits](../atl/reference/cprimitiveelementtraits-class.md)此类提供由基元数据类型组成的集合类的默认方法和函数。

- [CRBMap](../atl/reference/crbmap-class.md)此类表示使用 Red-黑色二进制树的映射结构。

- [CRBMultiMap](../atl/reference/crbmultimap-class.md)此类表示一个映射结构，该结构允许每个键与多个值相关联，同时使用 Red-黑色二进制树。

- [CRBTree](../atl/reference/crbtree-class.md)此类提供用于创建和使用红黑树的方法。

- [CSimpleArray](../atl/reference/csimplearray-class.md)此类提供用于管理简单数组的方法。

- [CSimpleArrayEqualHelper](../atl/reference/csimplearrayequalhelper-class.md)此类是[CSimpleArray](../atl/reference/csimplearray-class.md)类的帮助器。

- [CSimpleArrayEqualHelperFalse](../atl/reference/csimplearrayequalhelperfalse-class.md)此类是[CSimpleArray](../atl/reference/csimplearray-class.md)类的帮助器。

- [CSimpleMap](../atl/reference/csimplemap-class.md)此类提供对简单映射数组的支持。

- [CSimpleMapEqualHelper](../atl/reference/csimplemapequalhelper-class.md)此类是[CSimpleMap](../atl/reference/csimplemap-class.md)类的帮助器。

- [CSimpleMapEqualHelperFalse](../atl/reference/csimplemapequalhelperfalse-class.md)此类是[CSimpleMap](../atl/reference/csimplemap-class.md)类的帮助器。

- [CStringElementTraits](../atl/reference/cstringelementtraits-class.md)此类提供由存储`CString`对象的集合类使用的静态函数。

- [CStringElementTraitsI](../atl/reference/cstringelementtraitsi-class.md)此类提供与集合类对象中存储的字符串相关的静态函数。 它类似于[CStringElementTraits](../atl/reference/cstringelementtraits-class.md)，但执行不区分大小写的比较。

- [CStringRefElementTraits](../atl/reference/cstringrefelementtraits-class.md)此类提供与集合类对象中存储的字符串相关的静态函数。 字符串对象作为引用处理。

## <a name="related-articles"></a>相关文章

[ATL 集合类](../atl/atl-collection-classes.md)

## <a name="see-also"></a>请参阅

[类概述](../atl/atl-class-overview.md)<br/>
[集合类](../atl/atl-collection-classes.md)
