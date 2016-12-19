---
title: "ATL Copy Policy Classes | Microsoft Docs"
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
  - "_Copy class"
  - "_CopyInterface class"
  - "类 [C++], copy policy"
  - "copy policy classes [C++]"
  - "数据 [C++], ATL"
ms.assetid: 06704b68-d318-4c5d-a65b-71457fe9d00d
caps.latest.revision: 13
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL Copy Policy Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

复制策略选件类是用于的 [实用工具选件类](../atl/utility-classes.md) 初始化，复制和删除数据。  复制策略选件类可以定义任意数据的副本语义和定义差异数据类型之间的转换。  
  
 ATL在其以下模板的实现使用复制策略选件类:  
  
-   [CComEnumImpl](../atl/reference/ccomenumimpl-class.md)  
  
-   [IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)  
  
-   [ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)  
  
 通过封装必需的信息复制或将可作为模板参数的复制策略选件类的数据，ATL开发人员提供了这些选件类的极端可重用性。  例如，如果使用了，任何任意数据类型，需要实现集合，您需要提供的所有适用于复制策略;您不必相关实现集合的代码。  
  
## 定义  
 按照定义，提供下列静态函数的选件类是复制策略选件类:  
  
 `static void init(` `DestinationType` `* p);`  
  
 `static HRESULT copy(` `DestinationType` `* pTo, const`  `SourceType` `* pFrom);`  
  
 `static void destroy(` `DestinationType` `* p);`  
  
 可以在每次复制策略的任意数据类型替换类型 `DestinationType` 和 *SourceType*。  
  
> [!NOTE]
>  虽然可以定义复制策略适用于任何任意数据类型，在ATL代码的选件类中使用类应当限制有意义的类型。  例如，那么，当使用ATL的集合或枚举实现的复制策略选件类，`DestinationType` 必须是可用作参数COM接口方法的类型。  
  
 使用 **init** 初始化数据、 **copy** 到复制数据和 **destroy** 释放数据。  初始化的确切含义，复制和析构是复制策略选件类中的字段，并根据所涉及的数据类型而异。  
  
 具有使用和实现的两个要求复制策略选件类:  
  
-   为 **copy** 的第一个参数必须只接收指向使用 **init**，即先前初始化的数据。  
  
-   **destroy** 必须只接收指向先前已初始化使用 **init** 或通过 **copy**复制的数据。  
  
## 标准实现  
 在 **\_Copy** 和 **\_CopyInterface** 模板选件类的形式，ATL提供两选件复制策略类:  
  
-   **\_Copy** 选件类允许同类仅复制\(在数据类型之间的转换不是\)，因为它只提供一个模板参数指定 `DestinationType` 和 *SourceType*。  此模板的泛型实现不包含初始化或析构代码并使用 `memcpy` 复制数据。  ATL为 **VARIANT**、 `LPOLESTR`，**OLEVERB**和 **CONNECTDATA** 还提供 **\_Copy** 的专用化数据类型。  
  
-   在标准COM规则之后，**\_CopyInterface** 选件类提供复制的接口指针提供的实现。  再次此选件类允许同类仅复制，因此，它使用简单的赋值和调用 `AddRef` 执行副本。  
  
## 自定义实现  
 通常，您需要定义您异类复制的副本策略选件类\(即在数据类型之间的转换\)。  对于自定义复制策略选件类的一些示例，请查看在 [ATLCollections](../top/visual-cpp-samples.md) 示例中的文件VCUE\_Copy.h和VCUE\_CopyString.h。  这些文件包含两个模板复制策略选件类，`GenericCopy` 和 `MapCopy`，以及 `GenericCopy` 的专用化不同数据类型的。  
  
### GenericCopy  
 `GenericCopy` 允许您指定 *SourceType* 和 `DestinationType` 用作模板参数。  这是 `GenericCopy` 选件类的最通用的窗体。VCUE\_Copy.h的:  
  
 [!code-cpp[NVC_ATL_COM#30](../atl/codesnippet/CPP/atl-copy-policy-classes_1.h)]  
  
 VCUE\_Copy.h还包含此选件类的以下专用化: `GenericCopy<BSTR>`，`GenericCopy<VARIANT, BSTR>`，`GenericCopy<BSTR, VARIANT>`。  VCUE\_CopyString.h 包含用于从 **std::string**s: `GenericCopy<std::string>`、`GenericCopy<VARIANT, std::string>` 和 `GenericCopy<BSTR, std::string>` 进行复制的专用化。  可以通过提供自己的进一步专用化引发 `GenericCopy`。  
  
### MapCopy  
 `MapCopy` 假定，复制的数据在STL样式映射将存储，因此，它允许您指定该数据存储和目标类型映射的类型。  选件类的实现使用 *MapType* 选件类提供的typedef确定源数据的类型和调用相应的 `GenericCopy` 选件类。  此选件类的专用化不是必需的。  
  
 [!code-cpp[NVC_ATL_COM#31](../atl/codesnippet/CPP/atl-copy-policy-classes_2.h)]  
  
## 请参阅  
 [Implementing an STL\-Based Collection](../atl/implementing-an-stl-based-collection.md)   
 [ATLCollections示例](../top/visual-cpp-samples.md)