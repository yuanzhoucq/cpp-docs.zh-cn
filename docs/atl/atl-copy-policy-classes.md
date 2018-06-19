---
title: ATL 复制策略类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data [C++], ATL
- classes [C++], copy policy
- copy policy classes [C++]
- _Copy class
- _CopyInterface class
ms.assetid: 06704b68-d318-4c5d-a65b-71457fe9d00d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34b9ed5dca45633a5ab980d38b8a7cda151f5dc7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358522"
---
# <a name="atl-copy-policy-classes"></a>ATL 复制策略类
复制策略类是[实用工具类](../atl/utility-classes.md)用于初始化，复制和删除数据。 复制策略类允许你定义复制语义的任何类型的数据，并以不同的数据类型间定义对话。  
  
 ATL 使用复制策略类在其实现中的以下模板：  
  
-   [CComEnumImpl](../atl/reference/ccomenumimpl-class.md)  
  
-   [IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)  
  
-   [ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)  
  
 通过将封装复制或转换可以作为模板自变量传递的复制策略类中的数据所需的信息，ATL 开发人员提供用于这些类的极端可重用性。 例如，如果你需要实现使用的任意数据类型的集合，只需提供是适当的复制策略;你永远不需要 touch 实现集合的代码。  
  
## <a name="definition"></a>定义  
 根据定义，一个类，提供以下静态函数是一个复制策略类：  
  
 `static void init(` `DestinationType` `* p);`  
  
 `static HRESULT copy(` `DestinationType` `* pTo, const`  `SourceType` `* pFrom);`  
  
 `static void destroy(` `DestinationType` `* p);`  
  
 你可以替代的类型，`DestinationType`和*SourceType*具有每个复制策略的任意数据类型。  
  
> [!NOTE]
>  尽管你可以定义的所有任意数据类型的复制策略类，使用 ATL 代码中的类应限制有意义的类型。 例如，当使用复制策略类，该类具有 ATL 的集合或枚举器实现`DestinationType`必须是可用作 COM 接口方法中的参数的类型。  
  
 使用**init**初始化数据，**复制**复制数据，和**销毁**以释放数据。 初始化的精确意义、 复制和销毁都在域复制策略类和涉及的数据类型而异。  
  
 有两个要求的使用及复制策略类的实现：  
  
-   第一个参数**复制**必须仅接收指向以前初始化使用的数据的指针**init**。  
  
-   **销毁**必须只接收指向以前初始化使用的数据的指针**init**或通过复制**复制**。  
  
## <a name="standard-implementations"></a>标准的实现  
 ATL 提供的窗体中的两个复制策略类 **_Copy**和 **_CopyInterface**模板类：  
  
-   **_Copy**类允许同类仅在复制 （不数据类型之间的转换） 因为它仅提供单个模板参数同时指定`DestinationType`和*SourceType*。 此模板的泛型实现不包含任何初始化或析构的代码，并使用`memcpy`将数据复制。 ATL 还提供了专用化 **_Copy**为**VARIANT**， `LPOLESTR`， **OLEVERB**，和**次 CONNECTDATA**数据类型。  
  
-   **_CopyInterface**类提供复制遵循标准的 COM 规则的接口指针的实现。 再一次此类允许仅同类复制，因此它使用简单的赋值和调用`AddRef`来进行复制。  
  
## <a name="custom-implementations"></a>自定义实现  
 通常情况下，你将需要定义您自己的复制策略类对于异类复制 （即，数据类型之间的转换）。 有关自定义的复制策略类的一些示例，查看文件 VCUE_Copy.h 和中的 VCUE_CopyString.h [ATLCollections](../visual-cpp-samples.md)示例。 这些文件包含两个模板复制策略类，`GenericCopy`和`MapCopy`，外加一个数字的专用化`GenericCopy`个不同数据类型。  
  
### <a name="genericcopy"></a>Genericcopy 专用化  
 `GenericCopy` 允许你指定*SourceType*和`DestinationType`作为模板自变量。 下面是最常见形式`GenericCopy`VCUE_Copy.h 类：  
  
 [!code-cpp[NVC_ATL_COM#30](../atl/codesnippet/cpp/atl-copy-policy-classes_1.h)]  
  
 VCUE_Copy.h 还包含此类的以下的专用化： `GenericCopy<BSTR>`， `GenericCopy<VARIANT, BSTR>`， `GenericCopy<BSTR, VARIANT>`。 VCUE_CopyString.h 包含用于将从复制的专用化**std:: string**s: `GenericCopy<std::string>`， `GenericCopy<VARIANT, std::string>`，和`GenericCopy<BSTR, std::string>`。 你可以增强`GenericCopy`通过进一步提供你自己的专用化。  
  
### <a name="mapcopy"></a>MapCopy  
 `MapCopy` 假定正在复制的数据存储到 c + + 标准库样式映射中，因此它允许你指定的地图在其中的数据存储和目标类型的类型。 类的实现只需使用提供的 typedef *MapType*类以确定源数据的类型，并调用适当`GenericCopy`类。 不需要此类的任何专用化。  
  
 [!code-cpp[NVC_ATL_COM#31](../atl/codesnippet/cpp/atl-copy-policy-classes_2.h)]  
  
## <a name="see-also"></a>请参阅  
 [实现 c + + 标准库基于集合](../atl/implementing-an-stl-based-collection.md)   
 [ATLCollections 示例](../visual-cpp-samples.md)

