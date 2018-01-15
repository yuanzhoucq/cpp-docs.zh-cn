---
title: "从 CObject 派生类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CObject
dev_langs: C++
helpviewer_keywords:
- DECLARE_DYNCREATE macro [MFC]
- DECLARE_SERIAL macro [MFC]
- macros [MFC], serialization
- serialization [MFC], macros
- DECLARE_DYNAMIC macro [MFC]
- derived classes [MFC], from CObject
- CObject class [MFC], deriving serializable classes
- CObject class [MFC], deriving from
ms.assetid: 5ea4ea41-08b5-4bd8-b247-c5de8c152a27
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 97e151d8c3ec44286807baf5e68d4e4eac17e306
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="deriving-a-class-from-cobject"></a>从 CObject 派生类
本指南介绍了从派生类所必需的最小步骤[CObject](../mfc/reference/cobject-class.md)。 其他`CObject`类文章介绍利用特定于所需的步骤`CObject`功能，如序列化和诊断的调试支持。  
  
 在讨论`CObject`，经常使用术语"接口文件"和"实现文件"。 接口文件 (通常称为标头文件中，或。H 文件） 包含的类声明和使用类所需的任何其他信息。 实现文件 （或。CPP 文件） 包含类定义，以及实现类成员函数的代码。 例如，对于名为的类`CPerson`，通常将创建名为 PERSON 接口文件。H 和实现文件名为 PERSON。CPP。 但是，对于某些将不会共享在应用程序之间的较小类，它是有时更轻松地将接口和实现到单个合并。CPP 文件。  
  
 你可以从选择的功能的四个级别派生类时`CObject`:  
  
-   基本功能： 不支持运行时类信息或序列化但包括诊断内存管理。  
  
-   基本功能以及支持运行时类信息。  
  
-   基本功能以及支持运行时类信息和动态创建。  
  
-   基本功能以及支持运行时类信息、 动态创建和序列化。  
  
 如果预计以后需要序列，用于重复使用 （这些更高版本将用作基类） 的类应至少会包括运行时类支持和序列化支持。  
  
 通过使用特定的声明和实现宏的声明和实现派生自的类中选择的功能级别`CObject`。  
  
 下表显示了用于支持序列化和运行时信息的宏之间的关系。  
  
### <a name="macros-used-for-serialization-and-run-time-information"></a>用于序列化和运行时信息的宏  
  
|使用的宏|CObject::IsKindOf|CRuntimeClass::<br /><br /> CreateObject|CArchive::operator >><br /><br /> CArchive::operator <<|  
|----------------|-----------------------|--------------------------------------|-------------------------------------------------------|  
|基本`CObject`功能|否|否|否|  
|`DECLARE_DYNAMIC`|是|No|否|  
|`DECLARE_DYNCREATE`|是|是|No|  
|`DECLARE_SERIAL`|是|是|是|  
  
#### <a name="to-use-basic-cobject-functionality"></a>若要使用基本 CObject 功能  
  
1.  使用常规 c + + 语法来派生您的类从`CObject`(或从派生自类`CObject`)。  
  
     下面的示例演示最简单的情况，则将派生的类从`CObject`:  
  
     [!code-cpp[NVC_MFCCObjectSample#1](../mfc/codesnippet/cpp/deriving-a-class-from-cobject_1.h)]  
  
 通常情况下，但是，你可能想要重写某些`CObject`的成员函数来处理新类的具体信息。 例如，你可能通常想要重写`Dump`函数`CObject`为您的类的内容提供调试输出。 有关如何重写的详细信息`Dump`，请参阅文章[诊断： 转储对象内容](http://msdn.microsoft.com/en-us/727855b1-5a83-44bd-9fe3-f1d535584b59)。 你可能还想要重写`AssertValid`函数`CObject`以提供自定义的测试，以验证数据成员的类对象的一致性。 有关如何重写的说明`AssertValid`，请参阅[MFC ASSERT_VALID 和 CObject::AssertValid](http://msdn.microsoft.com/en-us/7654fb75-9e9a-499a-8165-0a96faf2d5e6)。  
  
 文章[指定级别的功能](../mfc/specifying-levels-of-functionality.md)说明如何指定其他级别的功能，包括运行时类信息、 动态对象创建和序列化。  
  
## <a name="see-also"></a>请参阅  
 [使用 CObject](../mfc/using-cobject.md)

