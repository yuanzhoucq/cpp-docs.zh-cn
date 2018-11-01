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
ms.openlocfilehash: 535bd1a3129bab15f546f6a82d77cf4e152fc605
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452749"
---
# <a name="atl-copy-policy-classes"></a>ATL 复制策略类

是复制策略类[实用程序类](../atl/utility-classes.md)用于初始化，复制和删除数据。 复制策略类允许您定义的任何类型的数据，复制语义，并定义不同的数据类型之间的转换。

ATL 使用复制策略类在其实现中的以下模板：

- [CComEnumImpl](../atl/reference/ccomenumimpl-class.md)

- [IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)

- [ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)

通过封装复制或转换可以作为模板自变量传递的复制策略类中的数据所需的信息，ATL 开发人员提供了有关这些类的极端可重用性。 例如，如果您需要实现使用任意数据类型的集合，需要提供是适当的复制策略;无需接触实现集合的代码。

## <a name="definition"></a>定义

根据定义，提供以下静态函数的类是一个复制策略类：

`static void init(` `DestinationType` `* p);`

`static HRESULT copy(` `DestinationType` `* pTo, const`  `SourceType` `* pFrom);`

`static void destroy(` `DestinationType` `* p);`

您可以替换类型`DestinationType`并*SourceType*与每个复制策略的任意数据类型。

> [!NOTE]
>  尽管可以定义为任何任意数据类型的复制策略类，但使用 ATL 代码中的类应限制有意义的类型。 例如，当使用复制策略类使用 ATL 的集合或枚举器实现`DestinationType`必须可用作 COM 接口方法中的参数的类型。

使用**init**若要初始化的数据，**副本**复制数据，并**销毁**来释放数据。 初始化的精确意义、 复制和析构的复制策略类域和涉及的数据类型而异。

有两个要求的使用和复制策略类的实现：

- 第一个参数**副本**必须仅接收指向前面初始化使用的数据的指针**init**。

- **销毁**必须只会接收到前面初始化使用的数据的指针**init**或通过复制**副本**。

## <a name="standard-implementations"></a>标准实现

ATL 提供了两个复制策略类中的窗体`_Copy`和`_CopyInterface`模板类：

- `_Copy`类允许同类仅复制 （不在数据类型之间的转换） 因为它仅提供单个模板参数来指定这两个`DestinationType`并*SourceType*。 此模板的泛型实现不包含任何初始化或破坏代码，并使用`memcpy`复制数据。 ATL 还提供的专用化`_Copy`变体、 LPOLESTR、 OLEVERB 和次 CONNECTDATA 数据类型。

- `_CopyInterface`类提供了用于复制接口指针遵循标准的 COM 规则实现。 再一次此类允许只同类复制，因此它使用简单的赋值和调用`AddRef`执行复制。

## <a name="custom-implementations"></a>自定义实现

通常情况下，你将需要定义您自己的异类复制 （即，数据类型之间的转换） 的复制策略类。 有关自定义复制策略类的一些示例，看看 VCUE_Copy.h 和 VCUE_CopyString.h 中的文件[ATLCollections](../visual-cpp-samples.md)示例。 这些文件包含两个模板复制策略类，`GenericCopy`并`MapCopy`，以及数目的专用化`GenericCopy`不同数据类型。

### <a name="genericcopy"></a>Genericcopy 专用化

`GenericCopy` 允许您指定*SourceType*和`DestinationType`作为模板参数。 下面是常见的形式的`GenericCopy`VCUE_Copy.h 类：

[!code-cpp[NVC_ATL_COM#30](../atl/codesnippet/cpp/atl-copy-policy-classes_1.h)]

VCUE_Copy.h 还包含此类的以下专用化： `GenericCopy<BSTR>`， `GenericCopy<VARIANT, BSTR>`， `GenericCopy<BSTR, VARIANT>`。 VCUE_CopyString.h 包含用于从复制的专用化**std:: string**s: `GenericCopy<std::string>`， `GenericCopy<VARIANT, std::string>`，和`GenericCopy<BSTR, std::string>`。 可增强`GenericCopy`通过进一步提供你自己的专用化。

### <a name="mapcopy"></a>MapCopy

`MapCopy` 假定要复制的数据存储到 c + + 标准库-style 映射，因此它允许您指定的映射，在其中存储数据的目标类型的类型。 类的实现仅使用提供的 typedef *MapType*类来确定的源数据类型，并调用适当`GenericCopy`类。 不需要此类的任何专用化。

[!code-cpp[NVC_ATL_COM#31](../atl/codesnippet/cpp/atl-copy-policy-classes_2.h)]

## <a name="see-also"></a>请参阅

[实现基于 C++ 标准库的集合](../atl/implementing-an-stl-based-collection.md)<br/>
[ATLCollections 示例](../visual-cpp-samples.md)

