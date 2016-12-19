---
title: "Implementing an STL-Based Collection | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ICollectionOnSTLImpl interface"
ms.assetid: 6d49f819-1957-4813-b074-3f12c494d8ca
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Implementing an STL-Based Collection
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL提供 `ICollectionOnSTLImpl` 接口使您可以快速实现标准模板库\(STL\) \-在对象的基于集合接口。  若要了解本选件类的工作方式，使用此选件类实现一个只读集合面向的自动化客户端中通过简单示例\(见下\)将工作。  
  
 代码示例是从 [ATLCollections示例](../top/visual-cpp-samples.md)。  
  
 若要完成此过程，您需要:  
  
-   [生成新的简单对象](#vccongenerating_an_object)。  
  
-   生成的接口的[编辑IDL文件](#vcconedit_the_idl)。  
  
-   描述如何存储集合项，以及如何的[创建五个typedef](#vcconstorage_and_exposure_typedefs) 将在客户端通过COM接口。  
  
-   [创建复制策略选件类的两typedef](#vcconcopy_classes)。  
  
-   [创建枚举数和集合实现的typedef](#vcconenumeration_and_collection)。  
  
-   [编辑向导生成的C\+\+代码使用集合typedef](#vcconedit_the_generated_code)。  
  
-   [添加代码以填充集合](#vcconpopulate_the_collection)。  
  
##  <a name="vccongenerating_an_object"></a> 生成新的简单对象  
 创建新项目，确保清除在应用程序设置下面的属性框。  使用ATL添加选件类对话框并添加简单对象向导生成调用 `Words`的简单对象。  确保调用 `IWords` 自己的生成。  生成的选件类的对象将用于表示字\(即字符串\)的集合。  
  
##  <a name="vcconedit_the_idl"></a> 编辑IDL文件  
 现在，打开IDL文件并添加必要的三个属性将 `IWords` 变成只读集合接口，如下所示:  
  
 [!code-cpp[NVC_ATL_COM#24](../atl/codesnippet/CPP/implementing-an-stl-based-collection_1.idl)]  
  
 这是旨在的只读集合接口的标准窗体考虑了自动化客户端。  此接口定义计算的注释对应于下面注释:  
  
1.  集合接口通过 **IDispatch::Invoke**通常是双重接口的，因为自动化客户端访问 `_NewEnum` 属性。  但是，自动化客户端通过vtable访问剩余方法，因此，双重接口否则最好是调度接口。  
  
2.  如果一个双重接口或调度接口不是扩展在运行时\(也就是说您不会通过 **IDispatch::Invoke**提供额外的方法或属性\)，应将 **nonextensible** 特性应用于定义。  此特性允许自动化客户端执行完整的代码验证在编译时。  在这种情况下，接口不应扩展的。  
  
3.  如果您希望自动化客户端可以使用此属性，正确的DISPID非常重要。  （请注意只有在 **DISPID\_NEWENUM**的一个下划线。）  
  
4.  可以提供任何值作为 **Item** 属性的DISPID。  但是，**Item** 通常使用 **DISPID\_VALUE** 使其成为默认属性集合。  这允许自动化客户端引用该属性，而无需显式命名为。  
  
5.  用于 **Item** 属性的返回值的数据类型是存储在集合中的项的类型，就COM客户端而言。  接口返回字符串，因此，应使用标准COM字符串类型，`BSTR`。  您不久，将看到您在不同的布局以在内部存储数据。  
  
6.  用于 **Count** 属性的DISPID的值完全是任意的。  如果没有此属性的标准DISPID。  
  
##  <a name="vcconstorage_and_exposure_typedefs"></a> 创建存储和风险的Typedef  
 对于集合接口中定义，您需要决定如何将存储数据，因此，数据如何通过枚举器将显示。  
  
 在许多的typedef形式，这些问题的答案可以提供，可以在标头文件顶部附近您新创建的选件类中添加:  
  
 [!code-cpp[NVC_ATL_COM#25](../atl/codesnippet/CPP/implementing-an-stl-based-collection_2.h)]  
  
 在这种情况下，将将数据存储为 **std::string**s. **std::vector**。  **std::vector** 是的行为与托管数组的STL容器选件类。  **std::string** 是标准C\+\+库的字符串选件类。  这些选件类便于与字符串一起使用的集合。  
  
 因为Visual Basic支持此接口的成功很重要，`_NewEnum` 属性返回的枚举数必须支持 **IEnumVARIANT** 接口。  这是Visual Basic了解的唯一枚举器接口。  
  
##  <a name="vcconcopy_classes"></a> 创建复制策略选件类的Typedef  
 您创建已在目前的typedef提供需要创建副本选件类的进一步typedef将由枚举数和集合使用的所有信息:  
  
 [!code-cpp[NVC_ATL_COM#26](../atl/codesnippet/CPP/implementing-an-stl-based-collection_3.h)]  
  
 在此示例中，您在VCUE\_Copy.h和VCUE\_CopyString.h可以使用中定义的自定义 `GenericCopy` 选件类从 [ATLCollections](../top/visual-cpp-samples.md) 示例。  在其他代码可以使用此选件类，但是，您可能需要定义 `GenericCopy` 的进一步专用化支持用于收集的数据类型。  有关更多信息，请参见 [ATL复制策略类选件](../atl/atl-copy-policy-classes.md)。  
  
##  <a name="vcconenumeration_and_collection"></a> 创建枚举和集合的Typedef  
 在typedef形式，现在需要所有模板的参数专用此情况的 `CComEnumOnSTL` 和 `ICollectionOnSTLImpl` 选件类提供的。  为了简化使用专用化，请再创建两个函数如下所示:  
  
 [!code-cpp[NVC_ATL_COM#27](../atl/codesnippet/CPP/implementing-an-stl-based-collection_4.h)]  
  
 现在 `CollectionType` 是实现前面定义的 `IWords` 接口 `ICollectionOnSTLImpl` 的专用化的同义词并提供支持 **IEnumVARIANT**的枚举器。  
  
##  <a name="vcconedit_the_generated_code"></a> 编辑向导生成的代码  
 现在必须从 `CollectionType` typedef表示的接口实现派生 `CWords` 而不是 `IWords`，如下所示:  
  
 [!code-cpp[NVC_ATL_COM#28](../atl/codesnippet/CPP/implementing-an-stl-based-collection_5.h)]  
  
##  <a name="vcconpopulate_the_collection"></a> 添加代码以填充集合  
 剩下的唯一事情是用数据填充矢量。  在此简单示例中，可以添加几个单词到构造函数的集合选件class ":  
  
 [!code-cpp[NVC_ATL_COM#29](../atl/codesnippet/CPP/implementing-an-stl-based-collection_6.h)]  
  
 现在，可以测试与所选的客户端代码。  
  
## 请参阅  
 [集合和枚举数](../atl/atl-collections-and-enumerators.md)   
 [ATLCollections示例](../top/visual-cpp-samples.md)   
 [ATL Copy Policy Classes](../atl/atl-copy-policy-classes.md)