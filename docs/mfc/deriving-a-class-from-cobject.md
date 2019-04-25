---
title: 从 CObject 派生类
ms.date: 11/04/2016
f1_keywords:
- CObject
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
ms.openlocfilehash: 26fdab5165ca098c5d7813ebf44983c261094449
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152054"
---
# <a name="deriving-a-class-from-cobject"></a>从 CObject 派生类

本文介绍从派生类所需的最小步骤[CObject](../mfc/reference/cobject-class.md)。 其他`CObject`类文章介绍了利用特定于所需的步骤`CObject`序列化和诊断的调试支持等功能。

在讨论`CObject`，经常使用术语"界面文件"和"实现文件"。 接口文件 (通常称为标头文件，或。H 文件） 包含的类声明和使用类所需的任何其他信息。 在实现文件 （或）。CPP 文件） 包含类定义和实现类成员函数的代码。 例如，对于名为的类`CPerson`，通常要创建一个名为 PERSON 的接口文件。H 和实现文件名称为 PERSON。CPP。 但是，对于将不会在应用程序之间共享某些较小类，是有时更轻松地将接口和实现为一个组合。CPP 文件。

可以从四个级别的功能时选择派生的类从`CObject`:

- 基本功能：不支持运行时类信息或序列化但包括诊断内存管理。

- 基本功能加上对运行时类信息的支持。

- 基本功能加上对运行时类信息和动态创建的支持。

- 基本功能加上对运行时类信息、 动态创建和序列化的支持。

便于重用 （这些更高版本将用作基类） 的类应至少包括运行时类支持和序列化支持，如果预计所有将来的序列化的需求。

通过使用特定的声明和实现宏的声明和实现从派生的类中选择的功能级别`CObject`。

下表显示了用于支持序列化和运行时信息的宏之间的关系。

### <a name="macros-used-for-serialization-and-run-time-information"></a>用于序列化和运行时信息的宏

|使用宏|CObject::IsKindOf|CRuntimeClass::<br /><br /> CreateObject|CArchive::operator >><br /><br /> CArchive::operator <<|
|----------------|-----------------------|--------------------------------------|-------------------------------------------------------|
|基本`CObject`功能|否|否|否|
|`DECLARE_DYNAMIC`|是|否|否|
|`DECLARE_DYNCREATE`|是|是|No|
|`DECLARE_SERIAL`|是|是|是|

#### <a name="to-use-basic-cobject-functionality"></a>若要使用基本 CObject 功能

1. 使用普通C++语法来派生您的类从`CObject`(或从派生自的类`CObject`)。

   下面的示例显示了简单的情况下，从类派生`CObject`:

   [!code-cpp[NVC_MFCCObjectSample#1](../mfc/codesnippet/cpp/deriving-a-class-from-cobject_1.h)]

通常情况下，但是，你可能想要重写某些`CObject`的成员函数来处理您的新类的具体情况。 例如，您可能通常想要重写`Dump`函数的`CObject`为您的类的内容提供调试输出。 有关如何重写的详细信息`Dump`，请参阅文章[转储对象的自定义](/previous-versions/visualstudio/visual-studio-2010/sc15kz85(v=vs.100))。 您可能还想要重写`AssertValid`函数的`CObject`以提供自定义测试以验证数据成员的类对象的一致性。 有关如何重写的说明`AssertValid`，请参阅[MFC ASSERT_VALID 和 CObject::AssertValid](reference/diagnostic-services.md#assert_valid)。

文章[指定级别的功能](../mfc/specifying-levels-of-functionality.md)介绍如何指定其他级别的功能，包括运行时类信息、 动态对象创建和序列化。

## <a name="see-also"></a>请参阅

[使用 CObject](../mfc/using-cobject.md)
