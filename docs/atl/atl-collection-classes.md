---
title: ATL 集合类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4594b87f07cd4d89937ba640d9a04aeacf2ef866
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359825"
---
# <a name="atl-collection-classes"></a>ATL 集合类
ATL 提供用于存储和访问数据的许多类。 你决定使用哪个类取决于多种因素，包括：  
  
-   要存储的数据量  
  
-   而不是在访问数据的性能的效率  
  
-   按索引或键访问数据的能力  
  
-   如何排列数据  
  
-   个人首选项  
  
## <a name="small-collection-classes"></a>小型集合类  
 ATL 提供用于处理数较少对象的以下的数组类。 但是，这些类是有限的专供内部 atl。 不建议你使用它们在程序中。  
  
|类|类型的数据存储|  
|-----------|--------------------------|  
|[CSimpleArray](../atl/reference/csimplearray-class.md)|实现处理数较少对象的数组类。|  
|[CSimpleMap](../atl/reference/csimplemap-class.md)|实现用于处理数较少对象的映射类。|  
  
## <a name="general-purpose-collection-classes"></a>通用集合类  
 下面的类实现数组、 列表和映射，并作为一般用途集合类提供：  
  
|类|类型的数据存储|  
|-----------|--------------------------|  
|[CAtlArray](../atl/reference/catlarray-class.md)|实现一个数组。|  
|[CAtlList](../atl/reference/catllist-class.md)|实现的列表。|  
|[CAtlMap](../atl/reference/catlmap-class.md)|实现一个映射结构，凭此可以通过键或值引用数据。|  
|[CRBMap](../atl/reference/crbmap-class.md)|实现一个映射结构，它使用红色黑色算法。|  
|[CRBMultiMap](../atl/reference/crbmultimap-class.md)|实现一个红色黑色多映射结构。|  
  
 这些类将捕获时，在调试版本使用的许多编程错误，但出于性能考虑，这些检查将无法执行的零售版本。  
  
## <a name="specialized-collection-classes"></a>专用的集合类  
 此外为管理的内存指针和接口指针提供了更多专用的集合类：  
  
|类|目标|  
|-----------|-------------|  
|[CAutoPtrArray](../atl/reference/cautoptrarray-class.md)|构造的智能指针的数组时，请提供有用的方法。|  
|[CAutoPtrList](../atl/reference/cautoptrlist-class.md)|构造的智能指针的列表时提供有用的方法。|  
|[CComUnkArray](../atl/reference/ccomunkarray-class.md)|存储`IUnknown`指针和旨在使用作为参数传递给[IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md)模板类。|  
|[CHeapPtrList](../atl/reference/cheapptrlist-class.md)|构造的堆指针的列表时提供有用的方法。|  
|[CInterfaceArray](../atl/reference/cinterfacearray-class.md)|构造的 COM 接口指针的数组时，请提供有用的方法。|  
|[CInterfaceList](../atl/reference/cinterfacelist-class.md)|构造的 COM 接口指针的列表时提供有用的方法。|  
  
## <a name="choosing-a-collection-class"></a>选择集合类  
 下表中所示，每个可用集合类提供不同的性能特征。  
  
-   列 2 和 3 描述了每个类的排序和访问特性。 在表中，术语“决定顺序”是指插入和删除项的顺序决定其在集合中的顺序；不是指项在其内容中的排序。 术语“索引检索”是指集合中的项可通过整数索引进行检索，这与典型数组中的项很相似。  
  
-   列 4 和 5 描述了每个类的性能。 在需要多次插入集合的应用程序中，插入速度可能特别重要；而对于其他应用程序，查找速度可能更为重要。  
  
-   列 6 描述了每个形状是否允许重复元素。  
  
-   按需完成该操作的集合中的元素数的时间之间的关系表示是给定的集合类操作的性能。 采用一段时间的操作，呈线性数目的元素增加描述为 o （n） 算法。 与此相反，采用较变得越来越没有作为数目的元素增加而增加的时间内的操作被描述为 O (日志 n) 算法。 因此，就性能来说，O (日志 n) 算法性能优于多地作为数目的元素增加 o （n） 算法。  
  
### <a name="collection-shape-features"></a>Collection Shape Features（集合形状特征）  
  
|形状|Ordered|编制索引|插入<br /><br /> 元素|搜索<br /><br /> 指定的元素|重复<br /><br /> 元素|  
|-----------|--------------|--------------|---------------------------|--------------------------------------|-----------------------------|  
|列表|是|否|快速 （常量时间）|慢速 o （n)|是|  
|数组|是|根据 int （常量时间）|如果在插入结束时，在哪个 case 常量时间内除慢速 o （n)|慢速 o （n)|是|  
|映射|否|由参数 （常量时间）|快速 （常量时间）|快速 （常量时间）|否（键）是（值）|  
|红色黑色映射|是 （由参数）|由参数 O (日志 n)|快速 O (日志 n)|快速 O (日志 n)|否|  
|红色黑色多重映射|是 （由参数）|由参数 O(log n) （每个键的多个值）|快速 O (日志 n)|快速 O (日志 n)|是 （每个键的多个值）|  
  
## <a name="using-ctraits-objects"></a>使用 CTraits 对象  
 ATL 集合类可以用于存储大量的用户定义的数据类型，因为它可用于将无法重写重要的功能，如比较。 这是使用 CTraits 类来实现的。  
  
 CTraits 类是相似，但比 MFC 集合类帮助器函数; 更加灵活请参阅[集合类帮助器](../mfc/reference/collection-class-helpers.md)有关详细信息。  
  
 构造时你的集合类，必须指定 CTraits 类的选项。 此类将包含将执行操作，如比较时由其他构成的集合类的方法调用的代码。 例如，如果你的列表对象包含自己用户定义的结构，你可能想要重新定义相等测试，以便仅将某些成员变量进行比较。 这种方式，列表对象的查找方法将运行中更有用的方式。  
  
## <a name="example"></a>示例  
  
### <a name="code"></a>代码  
 [!code-cpp[NVC_ATL_Utilities#112](../atl/codesnippet/cpp/atl-collection-classes_1.cpp)]  
  
## <a name="comments"></a>注释  
 CTraits 类的列表，请参阅[集合类](../atl/collection-classes.md)。  
  
 下图显示 CTraits 类的类层次结构。  
  
 ![集合类的特征层次结构](../atl/media/vctraitscollectionclasseshierarchy.gif "vctraitscollectionclasseshierarchy")  
  
## <a name="collection-classes-samples"></a>集合类示例  
 下面的示例演示的集合类：  
  
-   [MMXSwarm 示例](../visual-cpp-samples.md)  
  
-   [DynamicConsumer 示例](../visual-cpp-samples.md)  
  
-   [UpdatePV 示例](../visual-cpp-samples.md)  
  
-   [选框示例](../visual-cpp-samples.md)  
  
## <a name="see-also"></a>请参阅  
 [概念](../atl/active-template-library-atl-concepts.md)   
 [集合类](../atl/collection-classes.md)

