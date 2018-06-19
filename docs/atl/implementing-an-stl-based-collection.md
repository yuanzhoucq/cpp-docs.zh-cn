---
title: 实现 c + + 标准库基于集合 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ICollectionOnSTLImpl interface
ms.assetid: 6d49f819-1957-4813-b074-3f12c494d8ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 14a09f54598b525346a65b56a335711f114878cb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359670"
---
# <a name="implementing-a-c-standard-library-based-collection"></a>实现 c + + 标准库基于集合
ATL 提供`ICollectionOnSTLImpl`使您能够快速在你的对象上实施基于 c + + 标准库的集合接口的接口。 若要了解此类的工作原理，您将使用通过简单的示例 （见下面），使用此类实现旨在自动化客户端的只读集合。  
  
 代码示例摘自[ATLCollections 示例](../visual-cpp-samples.md)。  
  
 若要完成此过程，你将：  
  
-   [生成新的简单对象](#vccongenerating_an_object)。  
  
-   [编辑 IDL 文件](#vcconedit_the_idl)生成的接口。  
  
-   [创建五个 typedef](#vcconstorage_and_exposure_typedefs)描述的收集项的存储方式以及如何向客户端通过 COM 接口公开。  
  
-   [创建策略类的两个副本 typedef](#vcconcopy_classes)。  
  
-   [创建枚举器和集合实现的 typedef](#vcconenumeration_and_collection)。  
  
-   [编辑向导生成的 c + + 代码才能使用集合 typedef](#vcconedit_the_generated_code)。  
  
-   [添加代码以在集合中填入](#vcconpopulate_the_collection)。  
  
##  <a name="vccongenerating_an_object"></a> 生成新的简单对象  
 创建新项目，确保清除应用程序设置下的属性框。 使用 ATL 添加类对话框中，添加简单对象向导来生成一个简单的对象调用`Words`。 请确保双重接口调用`IWords`生成。 生成的类的对象将用于表示词 （即字符串） 的集合。  
  
##  <a name="vcconedit_the_idl"></a> 编辑 IDL 文件  
 现在，打开 IDL 文件并添加打开所需的三个属性`IWords`到只读集合接口，如下所示：  
  
 [!code-cpp[NVC_ATL_COM#24](../atl/codesnippet/cpp/implementing-an-stl-based-collection_1.idl)]  
  
 这是设计时牢记的自动化客户端的只读集合接口的标准窗体。 此接口定义中的编号的注释对应于下面的注释：  
  
1.  因为自动化客户端访问，集合接口是通常双重`_NewEnum`属性通过**idispatch:: Invoke**。 但是，自动化客户端可以访问通过 vtable，其余的方法，因此双重接口要优于调度接口。  
  
2.  如果双重接口或调度接口不会将扩展在运行时 (即，不会提供额外的方法或属性通过**idispatch:: Invoke**)，则应该应用**nonextensible**属性设为你的定义。 此属性允许自动化客户端执行完整的代码在编译时的验证。 在这种情况下，不应扩展接口。  
  
3.  如果你希望自动化客户端能够使用此属性很重要的正确的 DISPID。 (请注意，没有中的只有一个下划线**DISPID_NEWENUM**。)  
  
4.  你可以提供任何值的 DISPID 作为**项**属性。 但是，**项**通常使用**DISPID_VALUE**以使其集合的默认属性。 这允许自动化客户端不显式命名的情况下引用的属性。  
  
5.  用于的返回值的数据类型**项**属性是存储在集合中，就 COM 客户端所关注的项的类型。 接口返回的字符串，因此，应使用标准的 COM 字符串类型， `BSTR`。 你可以将数据存储在不同的格式内部很快就会看到如。  
  
6.  用于的 DISPID 值**计数**属性是完全任意。 为此属性没有标准 DISPID。  
  
##  <a name="vcconstorage_and_exposure_typedefs"></a> 为存储和公开创建 Typedefs  
 集合接口定义后，你需要决定将存储数据的方式，以及如何将枚举器通过公开数据。  
  
 可以在大量的 typedef，你可以为你新创建的类添加标头文件的顶部附近的窗体中提供这些问题的答案：  
  
 [!code-cpp[NVC_ATL_COM#25](../atl/codesnippet/cpp/implementing-an-stl-based-collection_2.h)]  
  
 在这种情况下，你将在其中存储数据作为**std:: vector**的**std:: string**s。 **std:: vector**是表现得像托管数组的 c + + 标准库容器类。 **std:: string**是 c + + 标准库的字符串类。 这些类使其易于使用的字符串的集合。  
  
 Visual Basic 支持对此接口的成功至关重要，因为返回的枚举数`_NewEnum`属性必须支持**IEnumVARIANT**接口。 这是 Visual Basic 被理解的唯一枚举器接口。  
  
##  <a name="vcconcopy_classes"></a> 为复制策略类创建 Typedefs  
 到目前为止创建的 typedef 提供你需要创建更多的枚举器和集合将使用的复制类的 typedef 的所有信息：  
  
 [!code-cpp[NVC_ATL_COM#26](../atl/codesnippet/cpp/implementing-an-stl-based-collection_3.h)]  
  
 在此示例中，你可以使用自定义`GenericCopy`VCUE_Copy.h 和从 VCUE_CopyString.h 中定义的类[ATLCollections](../visual-cpp-samples.md)示例。 你可以在其他代码中，使用此类，但你可能需要进一步定义的专用化`GenericCopy`以支持您自己的集合中使用的数据类型。 有关详细信息，请参阅[ATL 复制策略类](../atl/atl-copy-policy-classes.md)。  
  
##  <a name="vcconenumeration_and_collection"></a> 为枚举和集合创建 Typedefs  
 现在所有模板参数需要专用化`CComEnumOnSTL`和`ICollectionOnSTLImpl`typedef 的形式提供了这种情况下的类。 若要简化的使用的专用化，创建两个详细 typedef 如下所示：  
  
 [!code-cpp[NVC_ATL_COM#27](../atl/codesnippet/cpp/implementing-an-stl-based-collection_4.h)]  
  
 现在`CollectionType`是专用化的同义词`ICollectionOnSTLImpl`实现`IWords`接口前面定义和提供的枚举器支持的**IEnumVARIANT**。  
  
##  <a name="vcconedit_the_generated_code"></a> 编辑由向导生成的代码  
 现在必须派生`CWords`从所表示的接口实现`CollectionType`typedef 而非`IWords`，如下所示：  
  
 [!code-cpp[NVC_ATL_COM#28](../atl/codesnippet/cpp/implementing-an-stl-based-collection_5.h)]  
  
##  <a name="vcconpopulate_the_collection"></a> 添加代码以填充的集合  
 保持的唯一操作是填充具有数据的向量。 在此简单示例中，你可以将几个字添加到类的构造函数中的集合：  
  
 [!code-cpp[NVC_ATL_COM#29](../atl/codesnippet/cpp/implementing-an-stl-based-collection_6.h)]  
  
 现在，你可以使用所选的客户端来测试代码。  
  
## <a name="see-also"></a>请参阅  
 [集合和枚举数](../atl/atl-collections-and-enumerators.md)   
 [ATLCollections 示例](../visual-cpp-samples.md)   
 [ATL 复制策略类](../atl/atl-copy-policy-classes.md)

