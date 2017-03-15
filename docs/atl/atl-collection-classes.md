---
title: "ATL 集合类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "集合类"
  - "集合类, 关于集合类"
  - "集合类, 选择"
  - "ConstructElements 函数"
  - "CTraits 类"
  - "DestructElements 函数"
  - "SerializeElements 函数"
  - "traits 类"
ms.assetid: 4d619d46-5b4e-41dd-b9fd-e86b1fbc00b5
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# ATL 集合类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL用于存储和访问数据提供了许多选件类。  要选件类您决定使用取决于多种因素，包括:  
  
-   要存储的数据量。  
  
-   效率与访问数据的性能  
  
-   访问的能力数据按索引或由键  
  
-   该数据如何命令  
  
-   个人喜好  
  
## 小的集合选件类  
 ATL提供了以下数组选件类少量的对象。  但是，这些选件类是有限和内部设计为使用由ATL。  建议不要在程序中使用它们。  
  
|类|数据存储区的类型|  
|-------|--------------|  
|[CSimpleArray](../atl/reference/csimplearray-class.md)|实现托管数组选件类少量的对象。|  
|[CSimpleMap](../atl/reference/csimplemap-class.md)|实现处理的映射选件类少量的对象。|  
  
## 泛型集合类选件  
 在泛型集合类，如类实现数组，列表和映射和提供:  
  
|类|数据存储区的类型|  
|-------|--------------|  
|[CAtlArray](../atl/reference/catlarray-class.md)|实现一个数组。|  
|[CAtlList](../atl/reference/catllist-class.md)|实现一个列表。|  
|[CAtlMap](../atl/reference/catlmap-class.md)|实现一个映射的结构，通过数据可由键或值引用。|  
|[CRBMap](../atl/reference/crbmap-class.md)|使用红色黑色算法，实现一映射机制。|  
|[CRBMultiMap](../atl/reference/crbmultimap-class.md)|实现红色黑色multimapping的结构。|  
  
 这些选件类将捕获许多编程错误，当使用调试生成，但是，为了性能缘故，这些检查在发布版本不执行任何操作。  
  
## 专用集合选件类  
 专用集合选件类为托管内存指针和接口指针还提供:  
  
|类|用途|  
|-------|--------|  
|[CAutoPtrArray](../atl/reference/cautoptrarray-class.md)|当构造一个数组智能指针时，提供有用的方法。|  
|[CAutoPtrList](../atl/reference/cautoptrlist-class.md)|当构造列出了智能指针时，提供有用的方法。|  
|[CComUnkArray](../atl/reference/ccomunkarray-class.md)|存储 `IUnknown` 指针和旨在用作参数 [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) 模板选件类。|  
|[CHeapPtrList](../atl/reference/cheapptrlist-class.md)|当构造列表堆指针时，提供有用的方法。|  
|[CInterfaceArray](../atl/reference/cinterfacearray-class.md)|当构造一个数组COM接口指针时，提供有用的方法。|  
|[CInterfaceList](../atl/reference/cinterfacelist-class.md)|当构造列表COM接口指针时，提供有用的方法。|  
  
## 选择集合类选件  
 每个可用的集合选件类提供不同的性能特征，如下表所示。  
  
-   列2和3描述每选件类的排序和访问属性。  在表中，“顺序”结尾意味着项插入和删除的顺序决定它们的集合中的顺序;并不意味着项目在它们的内容排序。  该术语“标记”意味着集合中的项可以由整数索引检索，这与在典型的数组的项目。  
  
-   列4和5描述每选件类的性能。  在需要许多插入到集合的应用程序，插入速度可能尤其重要;对于其他应用程序，查找速度可能更为重要。  
  
-   第6列描述每个形状是否允许重复元素。  
  
-   特定的集合选件类操作的性能显示基于时间之间的关系完成操作和元素数集合中的。  需要线性递增的时间的操作，则元素数目有所增加称为o\(n\)算法。  相反，需要如此增加的时间的操作，则元素数目有所增加称为O \(log n\)算法。  因此，就性能而言，O \(log n\)算法超过o\(n\)多算法，当元素数增加。  
  
### 集合形态功能  
  
|形状|排序?|标记?|插入<br /><br /> 元素|搜索<br /><br /> 指定的元素|重复<br /><br /> 元素?|  
|--------|---------|---------|---------------|------------------|----------------|  
|列表|是|否|优先\(常数的时间\)|降低o\(n\)|是|  
|数组|是|由int\(4\)常数的时间\)|降低o\(n\)除外，如果插入到末尾，在常数时情况下|降低o\(n\)|是|  
|映射|否|由键\(常数的时间\)|优先\(常数的时间\)|优先\(常数的时间\)|没有\(键\)是\(值\)|  
|红色黑色映射|是\(由键\)|由键O \(log n\)|快速O \(log n\)|快速O \(log n\)|否|  
|红色黑色基于|是\(由键\)|由键O \(log n\) \(一键多值\)|快速O \(log n\)|快速O \(log n\)|是\(一键多值\)|  
  
## 使用CTraits Objects  
 当ATL 集合选件类可用于存储大量用户定义的数据类型，可以重写重要功能\(如比较会很有用。  使用CTraits选件类，则实现。  
  
 CTraits选件类相似，但是，更为灵活，MFC集合类选件helper函数;请参见 [集合类帮助器](../mfc/reference/collection-class-helpers.md) 有关更多信息。  
  
 当编写您的集合选件类时，可以指定CTraits选件类的选项。  此选件类将包含将执行操作\(如比较，在调用没有其他方法组成集合选件类的代码。  例如，在中，如果列表对象包含您的用户定义的结构，您可能希望重新定义相等测试只比较某些成员变量。  这样，列表对象中查找方法将运行提供更有用的方式。  
  
## 示例  
  
### 代码  
 [!code-cpp[NVC_ATL_Utilities#112](../atl/codesnippet/CPP/atl-collection-classes_1.cpp)]  
  
## 注释  
 有关CTraits选件类的列表，请参见 [集合选件类](../atl/collection-classes.md)。  
  
 下图显示CTraits选件类的选件类层次结构。  
  
 ![集合类的特征层次结构](../atl/media/vctraitscollectionclasseshierarchy.png "vcTraitsCollectionClassesHierarchy")  
  
## 集合类示例  
 下面的示例演示集合选件类:  
  
-   [MMXSwarm示例](../top/visual-cpp-samples.md)  
  
-   [DynamicConsumer示例](../top/visual-cpp-samples.md)  
  
-   [UpdatePV示例](../top/visual-cpp-samples.md)  
  
-   [marquee示例](../top/visual-cpp-samples.md)  
  
## 请参阅  
 [概念](../atl/active-template-library-atl-concepts.md)   
 [集合类](../atl/collection-classes.md)