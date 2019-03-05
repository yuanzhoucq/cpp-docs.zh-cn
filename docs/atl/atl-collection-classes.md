---
title: ATL 集合类
ms.date: 11/19/2018
helpviewer_keywords:
- DestructElements function
- collection classes, choosing
- ConstructElements function
- SerializeElements function
- traits classes
- collection classes, about collection classes
- CTraits classes
- collection classes
ms.assetid: 4d619d46-5b4e-41dd-b9fd-e86b1fbc00b5
ms.openlocfilehash: 11da1dd7d72951d421d2600e3825e7cafe189240
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272095"
---
# <a name="atl-collection-classes"></a>ATL 集合类

ATL 提供许多类，用于存储和访问数据。 您决定使用哪个类取决于多种因素，包括：

- 要存储的数据量

- 中访问数据的性能与效率

- 按索引或键访问数据的能力

- 数据如何排序

- 个人首选项

## <a name="small-collection-classes"></a>小型集合类

ATL 提供以下数组类来处理数量较少的对象。 但是，这些类是有限的设计用于在内部由 atl。 不建议你使用它们在程序中。

|类|数据存储类型|
|-----------|--------------------------|
|[CSimpleArray](../atl/reference/csimplearray-class.md)|实现用于处理数量较少的对象数组类。|
|[CSimpleMap](../atl/reference/csimplemap-class.md)|实现映射类用于处理数量较少的对象。|

## <a name="general-purpose-collection-classes"></a>常规用途的集合类

下面的类实现数组、 列表和映射，将作为常规用途的集合类提供：

|类|数据存储类型|
|-----------|--------------------------|
|[CAtlArray](../atl/reference/catlarray-class.md)|实现一个数组。|
|[CAtlList](../atl/reference/catllist-class.md)|实现列表。|
|[CAtlMap](../atl/reference/catlmap-class.md)|实现映射结构，因此通过键或值引用数据。|
|[CRBMap](../atl/reference/crbmap-class.md)|实现使用红黑算法映射结构。|
|[CRBMultiMap](../atl/reference/crbmultimap-class.md)|实现红黑多映射结构。|

这些类将捕获时，在调试版本使用的许多编程错误，但出于性能考虑，这些检查不会执行在零售版本中。

## <a name="specialized-collection-classes"></a>专用的集合类

专用的集合类还提供用于管理内存的指针和接口指针：

|类|目标|
|-----------|-------------|
|[CAutoPtrArray](../atl/reference/cautoptrarray-class.md)|构造的智能指针的数组时，提供了有用的方法。|
|[CAutoPtrList](../atl/reference/cautoptrlist-class.md)|构造的智能指针的列表时提供有用的方法。|
|[CComUnkArray](../atl/reference/ccomunkarray-class.md)|存储`IUnknown`指针，它旨在用作参数[IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)模板类。|
|[CHeapPtrList](../atl/reference/cheapptrlist-class.md)|构造的堆指针的列表时提供有用的方法。|
|[CInterfaceArray](../atl/reference/cinterfacearray-class.md)|构造的 COM 接口指针的数组时，提供了有用的方法。|
|[CInterfaceList](../atl/reference/cinterfacelist-class.md)|构造的 COM 接口指针的列表时提供有用的方法。|

## <a name="choosing-a-collection-class"></a>选择集合类

下表中所示，每个可用性集合类提供不同的性能特征。

- 列 2 和 3 描述了每个类的排序和访问特性。 在表中，术语“决定顺序”是指插入和删除项的顺序决定其在集合中的顺序；不是指项在其内容中的排序。 术语“索引检索”是指集合中的项可通过整数索引进行检索，这与典型数组中的项很相似。

- 列 4 和 5 描述了每个类的性能。 在需要多次插入集合的应用程序中，插入速度可能特别重要；而对于其他应用程序，查找速度可能更为重要。

- 列 6 描述了每个形状是否允许重复元素。

- 给定的集合类操作的性能，以完成该操作和集合中的元素数所需的时间之间的关系。 操作花费的时间量的增加会线性数目的元素增加被描述为 o （n） 算法。 与此相反，采用一段时间，可降低为数目的元素增加提高的操作被描述为 O (log n) 算法。 因此，就性能来说，O (log n) 算法的优势要比作为数目的元素增加更多的 o （n） 算法。

### <a name="collection-shape-features"></a>Collection Shape Features（集合形状特征）

|形状|Ordered|编制索引|插入<br /><br /> 元素|搜索<br /><br /> 指定的元素|重复<br /><br /> 元素|
|-----------|--------------|--------------|---------------------------|--------------------------------------|-----------------------------|
|列表|是|否|快速 （常量时间）|慢速 o （n)|是|
|数组|是|根据 int （常量时间）|除了在末尾插入，在哪个 case 常量时间内缓慢 o （n）|慢速 o （n)|是|
|映射|否|由参数 （常量时间）|快速 （常量时间）|快速 （常量时间）|否（键）是（值）|
|红黑映射|是 （通过密钥）|由键 O (log n)|快速 O (log n)|快速 O (log n)|否|
|红黑多重映射|是 （通过密钥）|由键 O(log n) （每个键的多个值）|快速 O (log n)|快速 O (log n)|是 （每个键的多个值）|

## <a name="using-ctraits-objects"></a>使用 CTraits 对象

ATL 集合类可以用于存储大量的用户定义数据类型，因为它可用于将无法重写如比较重要的功能。 这是使用 CTraits 类实现的。

CTraits 类是相似，但比 MFC 集合类帮助器函数; 更灵活请参阅[集合类帮助器](../mfc/reference/collection-class-helpers.md)有关详细信息。

在构造时你的集合类，您可以指定 CTraits 类。 此类将包含将执行操作，如比较时调用的其他方法的集合类所组成的代码。 例如，如果列表对象中包含您的用户定义的结构，你可能想要重新定义相等性测试，以便只比较特定的成员变量。 这样一来，列表对象的 Find 方法将运行更多有用的方式。

## <a name="example"></a>示例

### <a name="code"></a>代码

[!code-cpp[NVC_ATL_Utilities#112](../atl/codesnippet/cpp/atl-collection-classes_1.cpp)]

## <a name="comments"></a>注释

CTraits 类的列表，请参阅[集合类](../atl/collection-classes.md)。

下图显示了 CTraits 类的类层次结构。

![集合类特征层次结构](../atl/media/vctraitscollectionclasseshierarchy.gif "的集合类特征层次结构")

## <a name="collection-classes-samples"></a>集合类示例

下面的示例演示的集合类：

- [MMXSwarm 示例](../visual-cpp-samples.md)

- [DynamicConsumer 示例](../visual-cpp-samples.md)

- [UpdatePV 示例](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)

- [字幕示例](../visual-cpp-samples.md)

## <a name="see-also"></a>请参阅

[概念](../atl/active-template-library-atl-concepts.md)<br/>
[集合类](../atl/collection-classes.md)
