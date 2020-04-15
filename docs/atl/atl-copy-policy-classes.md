---
title: ATL 复制策略类
ms.date: 11/04/2016
helpviewer_keywords:
- data [C++], ATL
- classes [C++], copy policy
- copy policy classes [C++]
- _Copy class
- _CopyInterface class
ms.assetid: 06704b68-d318-4c5d-a65b-71457fe9d00d
ms.openlocfilehash: f40f31124d4547076249a7459ac4b63cc25305d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317380"
---
# <a name="atl-copy-policy-classes"></a>ATL 复制策略类

复制策略类是用于初始化、复制和删除数据的[实用程序类](../atl/utility-classes.md)。 复制策略类允许您为任何类型的数据定义复制语义，并定义不同数据类型之间的转换。

ATL 在其实现以下模板时使用复制策略类：

- [CComEnumimpl](../atl/reference/ccomenumimpl-class.md)

- [伊纳姆翁斯特莱普](../atl/reference/ienumonstlimpl-class.md)

- [ICollectiononSTLimpl](../atl/reference/icollectiononstlimpl-class.md)

通过封装复制或转换数据所需的信息，这些数据可以作为模板参数传递，ATL 开发人员提供了这些类的极端可重用性。 例如，如果需要使用任何任意数据类型实现集合，则只需提供相应的复制策略;如果需要使用任意数据类型实现集合，则只需适当的复制策略。您永远不必触摸实现集合的代码。

## <a name="definition"></a>定义

根据定义，提供以下静态函数的类是复制策略类：

`static void init(` `DestinationType` `* p);`

`static HRESULT copy(` `DestinationType` `* pTo, const`  `SourceType` `* pFrom);`

`static void destroy(` `DestinationType` `* p);`

您可以将类型`DestinationType`和*SourceType*替换为每个复制策略的任意数据类型。

> [!NOTE]
> 尽管可以为任何任意数据类型定义复制策略类，但在 ATL 代码中使用类应限制有意义的类型。 例如，在将复制策略类与 ATL 的集合或枚举器实现一起使用时，`DestinationType`必须是一种类型，可以在 COM 接口方法中用作参数。

使用**init**初始化数据、**复制**以复制数据以及**销毁**以释放数据。 初始化、复制和销毁的确切含义是复制策略类的域，并且会根据所涉及的数据类型而变化。

关于复制策略类的使用和实现有两个要求：

- 要**复制**的第一个参数只能接收指向以前使用**init**初始化的数据的指针。

- **销毁**必须只接收指向以前使用**init**或通过**复制**复制的数据的指针。

## <a name="standard-implementations"></a>标准实现

ATL 以`_Copy`和`_CopyInterface`模板类的形式提供两个复制策略类：

- 该`_Copy`类只允许同质复制（数据类型之间不转换），因为它只提供一个模板参数来指定和`DestinationType` *SourceType*。 此模板的通用实现不包含初始化或销毁代码，并用于`memcpy`复制数据。 ATL 还提供 VARIANT、LPOLESTR、OLEVERB 和 CONNECTDATA 数据类型的`_Copy`专业化认证。

- 类`_CopyInterface`提供了一个实现，用于按照标准 COM 规则复制接口指针。 同样，此类只允许同质复制，因此它使用简单的赋值和调用`AddRef`来执行复制。

## <a name="custom-implementations"></a>自定义实现

通常，您需要为异构复制（即数据类型之间的转换）定义自己的复制策略类。 有关自定义复制策略类的一些示例，请查看[ATLCollections](../overview/visual-cpp-samples.md)示例中VCUE_Copy.h 和 VCUE_CopyString.h 的文件。 这些文件包含两个模板复制策略类，`GenericCopy`以及`MapCopy`，以及针对不同数据类型的`GenericCopy`多种专门化。

### <a name="genericcopy"></a>通用复制

`GenericCopy`允许您指定*SourceType*并作为`DestinationType`模板参数。 以下是 VCUE_Copy.h 类的最通用`GenericCopy`形式：

[!code-cpp[NVC_ATL_COM#30](../atl/codesnippet/cpp/atl-copy-policy-classes_1.h)]

VCUE_Copy.h 还包含此类的以下专门化： `GenericCopy<BSTR>`， `GenericCopy<VARIANT, BSTR>`. `GenericCopy<BSTR, VARIANT>` VCUE_CopyString.h 包含用于从**std：字符串**s 复制的专门`GenericCopy<std::string>`化`GenericCopy<VARIANT, std::string>`：`GenericCopy<BSTR, std::string>`和 。 您可以通过提供您自己的`GenericCopy`进一步专业化来增强。

### <a name="mapcopy"></a>地图复制

`MapCopy`假定要复制的数据存储在C++标准库样式映射中，因此允许您指定存储数据的地图类型和目标类型。 类的实现只是使用*MapType*类提供的 typedefs 来确定源数据类型并调用相应的`GenericCopy`类。 不需要此类的专业化化。

[!code-cpp[NVC_ATL_COM#31](../atl/codesnippet/cpp/atl-copy-policy-classes_2.h)]

## <a name="see-also"></a>另请参阅

[实现基于C++标准库集合](../atl/implementing-an-stl-based-collection.md)<br/>
[ATL集合示例](../overview/visual-cpp-samples.md)
