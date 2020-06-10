---
title: 从 CObject 派生类
ms.date: 11/04/2016
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
ms.openlocfilehash: f4c01538877d8517cf3394d9e0108ce3a9df2900
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621944"
---
# <a name="deriving-a-class-from-cobject"></a>从 CObject 派生类

本文介绍从[CObject](reference/cobject-class.md)派生类所需的最少步骤。 其他 `CObject` 类文章描述了利用特定 `CObject` 功能（如序列化和诊断调试支持）所需的步骤。

在的讨论中 `CObject` ，经常使用术语 "interface file" 和 "实现文件"。 接口文件（通常称为标头文件，或。H 文件）包含类声明以及使用类所需的任何其他信息。 实现文件（或。CPP 文件）包含类定义以及实现类成员函数的代码。 例如，对于名为的类 `CPerson` ，通常会创建一个名为 PERSON 的接口文件。H 和名为 PERSON 的实现文件。.CPP. 但是，对于不在应用程序之间共享的某些小型类，有时会更容易将接口和实现组合到一个中。CPP 文件。

从派生类时，可以从四个级别的功能中进行选择 `CObject` ：

- 基本功能：不支持运行时类信息或序列化，但包括诊断内存管理。

- 基本功能，并支持运行时类信息。

- 基本功能，还支持运行时类信息和动态创建。

- 基本功能，并支持运行时类信息、动态创建和序列化。

如果预计将来需要序列化，则为重用设计的类（稍后将用作基类的类）应至少包含运行时类支持和序列化支持。

使用派生自的类的声明和实现中的特定声明和实现宏，可以选择功能的级别 `CObject` 。

下表显示了用于支持序列化和运行时信息的宏之间的关系。

### <a name="macros-used-for-serialization-and-run-time-information"></a>用于序列化和运行时信息的宏

|使用的宏|CObject：： IsKindOf|CRuntimeClass：：<br /><br /> CreateObject|CArchive：： operator>><br /><br /> CArchive：： operator<<|
|----------------|-----------------------|--------------------------------------|-------------------------------------------------------|
|基本 `CObject` 功能|否|否|否|
|`DECLARE_DYNAMIC`|是|No|否|
|`DECLARE_DYNCREATE`|是|是|No|
|`DECLARE_SERIAL`|是|是|是|

#### <a name="to-use-basic-cobject-functionality"></a>使用基本 CObject 功能

1. 使用常规 c + + 语法从 `CObject` （或从派生的类）派生类 `CObject` 。

   下面的示例演示了中的类的派生情况最简单的情况 `CObject` ：

   [!code-cpp[NVC_MFCCObjectSample#1](codesnippet/cpp/deriving-a-class-from-cobject_1.h)]

不过，通常情况下，您可能希望重写一些 `CObject` 成员函数来处理您的新类的细节。 例如，你可能需要重写的 `Dump` 函数 `CObject` 以提供类内容的调试输出。 有关如何重写的详细信息 `Dump` ，请参阅文章[对象转储自定义](/previous-versions/visualstudio/visual-studio-2010/sc15kz85(v=vs.100))。 您可能还需要重写的 `AssertValid` 函数 `CObject` 以提供自定义的测试，以验证类对象的数据成员的一致性。 有关如何重写的说明 `AssertValid` ，请参阅[MFC ASSERT_VALID 和 CObject：： AssertValid](reference/diagnostic-services.md#assert_valid)。

[指定功能级别一](specifying-levels-of-functionality.md)文介绍了如何指定其他级别的功能，包括运行时类信息、动态对象创建和序列化。

## <a name="see-also"></a>另请参阅

[使用 CObject](using-cobject.md)
