---
title: 实现 c + + 标准库基于集合 |Microsoft Docs
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
ms.openlocfilehash: 4b6aa360229857e3c12322cb6579aa0dbbba53d9
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753235"
---
# <a name="implementing-a-c-standard-library-based-collection"></a>实现 c + + 标准库基于集合

ATL 提供`ICollectionOnSTLImpl`接口以使您能够快速在您的对象上实现基于 c + + 标准库的集合接口。 若要了解此类的工作原理，您可以通过一个简单示例 （下面），使用此类实现旨在自动化客户端的只读集合。

示例代码摘自[ATLCollections 示例](../visual-cpp-samples.md)。

若要完成此过程，你将：

- [生成新的简单对象](#vccongenerating_an_object)。

- [编辑 IDL 文件](#vcconedit_the_idl)为生成的接口。

- [创建五个 typedef](#vcconstorage_and_exposure_typedefs)描述如何将存储收集项以及如何向客户端通过 COM 接口公开。

- [创建两个 typedef，来复制策略类](#vcconcopy_classes)。

- [创建的枚举器和集合实现的 typedef](#vcconenumeration_and_collection)。

- [编辑由向导生成的 c + + 代码使用集合 typedef](#vcconedit_the_generated_code)。

- [添加代码以填充集合](#vcconpopulate_the_collection)。

##  <a name="vccongenerating_an_object"></a> 生成一个新的简单对象

创建新项目，确保清除应用程序设置下的属性框。 使用 ATL 添加类对话框中，添加简单对象向导来生成一个简单的对象调用`Words`。 请确保双重接口调用`IWords`生成。 生成的类的对象将用于表示词 （即，字符串） 的集合。

##  <a name="vcconedit_the_idl"></a> 编辑 IDL 文件

现在，打开 IDL 文件并添加启用所需的三个属性`IWords`到只读集合接口，如下所示：

[!code-cpp[NVC_ATL_COM#24](../atl/codesnippet/cpp/implementing-an-stl-based-collection_1.idl)]

这是设计为具有记住自动化客户端的只读集合接口的标准格式。 此接口定义中的编号的注释对应于下面的注释：

1. 因为自动化客户端访问的集合接口是通常双`_NewEnum`属性通过`IDispatch::Invoke`。 但是，自动化客户端可以访问通过 vtable，剩余的方法，因此双重接口要优于调度接口。

2. 如果双重接口或调度接口中，将不提供在运行时 (即，不会提供额外的方法或通过属性`IDispatch::Invoke`)，应该应用**nonextensible**属性为你的定义。 此属性允许自动化客户端执行完整的代码在编译时验证。 在这种情况下，不应扩展接口。

3. 如果你希望自动化客户端将无法使用此属性，则正确的 DISPID 至关重要。 （请注意 DISPID_NEWENUM 中已有一个下划线）。

4. 你可以提供任何值的 DISPID 作为`Item`属性。 但是，`Item`通常使用 DISPID_VALUE 来使其集合的默认属性。 这允许自动化客户端引用的属性，而无需显式命名。

5. 用于的返回值的数据类型`Item`属性是存储在集合中就 COM 客户端所关注的项的类型。 接口将返回字符串，因此，应使用标准 COM 字符串类型，BSTR。 你可以将数据存储在不同的格式在内部如稍后您将看到。

6. 使用的 DISPID 值`Count`是完全任意的属性。 为此属性没有标准 DISPID。

##  <a name="vcconstorage_and_exposure_typedefs"></a> 创建用于存储和曝光 Typedef

集合接口定义后，您需要决定如何将存储数据，以及如何通过枚举器公开的数据。

可以在数可以为您新创建的类添加标头文件的顶部附近的 typedef 的窗体中提供这些问题的答案：

[!code-cpp[NVC_ATL_COM#25](../atl/codesnippet/cpp/implementing-an-stl-based-collection_2.h)]

在这种情况下，将存储将数据作为**std:: vector**的**std:: string**s。 **std:: vector**是 c + + 标准库容器类的行为类似于托管数组。 **std:: string**是 c + + 标准库的字符串类。 这些类使其更易使用的字符串集合。

Visual Basic 支持对此接口的成功至关重要，因为返回的枚举数`_NewEnum`属性必须支持`IEnumVARIANT`接口。 这是 Visual Basic 所理解的唯一枚举数接口。

##  <a name="vcconcopy_classes"></a> 为复制策略类创建 Typedefs

到目前为止已创建的 typedef 提供您需要创建更多的枚举器和集合将使用的复制类类型定义的所有信息：

[!code-cpp[NVC_ATL_COM#26](../atl/codesnippet/cpp/implementing-an-stl-based-collection_3.h)]

在此示例中，可以使用自定义`GenericCopy`VCUE_Copy.h 和从 VCUE_CopyString.h 中定义的类[ATLCollections](../visual-cpp-samples.md)示例。 可以在其他代码中，使用此类，但可能需要进一步定义的专用化`GenericCopy`以支持使用自己的集合中的数据类型。 有关详细信息，请参阅[ATL 复制策略类](../atl/atl-copy-policy-classes.md)。

##  <a name="vcconenumeration_and_collection"></a> 为枚举和集合创建类型定义

现在所有模板参数专用化所需`CComEnumOnSTL`和`ICollectionOnSTLImpl`typedef 的形式提供了这种情况下的类。 若要简化的专用化使用，创建两个更多的 typedef，如下所示：

[!code-cpp[NVC_ATL_COM#27](../atl/codesnippet/cpp/implementing-an-stl-based-collection_4.h)]

现在`CollectionType`的专用化的同义词`ICollectionOnSTLImpl`实现`IWords`接口之前定义，并提供一个枚举数支持`IEnumVARIANT`。

##  <a name="vcconedit_the_generated_code"></a> 编辑由向导生成的代码

现在必须派生`CWords`所表示的接口实现`CollectionType`typedef 而非`IWords`，如下所示：

[!code-cpp[NVC_ATL_COM#28](../atl/codesnippet/cpp/implementing-an-stl-based-collection_5.h)]

##  <a name="vcconpopulate_the_collection"></a> 添加代码以填充的集合

保持的唯一事情是填充数据的向量。 在此简单示例中，可以将几个字添加到类的构造函数中的集合：

[!code-cpp[NVC_ATL_COM#29](../atl/codesnippet/cpp/implementing-an-stl-based-collection_6.h)]

现在，可以使用所选的客户端来测试代码。

## <a name="see-also"></a>请参阅

[集合和枚举数](../atl/atl-collections-and-enumerators.md)   
[ATLCollections 示例](../visual-cpp-samples.md)   
[ATL 复制策略类](../atl/atl-copy-policy-classes.md)

