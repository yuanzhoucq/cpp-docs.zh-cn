---
title: 访问运行时类信息
ms.date: 11/04/2016
helpviewer_keywords:
- CObject class [MFC], and RTTI
- CObject class [MFC], using IsKindOf method [MFC]
- run time [MFC], class information
- RUNTIME_CLASS macro [MFC]
- CObject class [MFC], using RUNTIME_CLASS macro [MFC]
- RTTI compiler option [MFC]
- CObject class [MFC], accessing run-time class information
- run time [MFC]
- IsKindOf method method [MFC]
- run-time class [MFC], accessing information
- classes [MFC], run-time class information
- run-time class [MFC]
- RUNTIME_CLASS macro, using
ms.assetid: 3445a9af-0bd6-4496-95c3-aa59b964570b
ms.openlocfilehash: a9f90640007f84c854d59cc27e0c38459c76fe46
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619189"
---
# <a name="accessing-run-time-class-information"></a>访问运行时类信息

本文说明了如何在运行时访问对象的类的相关信息。

> [!NOTE]
> MFC 不使用 Visual C++ 4.0 中引入的[运行时类型信息](../cpp/run-time-type-information.md)（RTTI）支持。

如果已从[cobject](reference/cobject-class.md)派生类并使用了**DECLARE**_**DYNAMIC**和 `IMPLEMENT_DYNAMIC` 、和， `DECLARE_DYNCREATE` `IMPLEMENT_DYNCREATE` 或者 `DECLARE_SERIAL` `IMPLEMENT_SERIAL` 在[从 CObject 派生类一](deriving-a-class-from-cobject.md)文中介绍了和宏，则 `CObject` 该类可以在运行时确定对象的确切类。

在需要函数参数的其他类型检查时，以及在必须基于对象的类编写特殊用途的代码时，此功能非常有用。 但是，通常建议不要使用此做法，因为它会复制虚函数的功能。

`CObject` 成员函数 `IsKindOf` 可用于确定某个特定对象是否属于某个指定类或者是否派生自某个特定类。 `IsKindOf` 的自变量是一个 `CRuntimeClass` 对象，您可以将 `RUNTIME_CLASS` 宏与类名一起使用来获取此对象。

### <a name="to-use-the-runtime_class-macro"></a>使用 RUNTIME_CLASS 宏

1. 将 `RUNTIME_CLASS` 与类名一起使用，如此处为 `CObject` 类所示的：

   [!code-cpp[NVC_MFCCObjectSample#4](codesnippet/cpp/accessing-run-time-class-information_1.cpp)]

您很少需要直接访问运行时类对象。 更常见的用法是将运行时类对象传递给 `IsKindOf` 函数，如下面的过程中所示。 `IsKindOf` 函数测试一个对象来确定它是否属于某个特定类。

#### <a name="to-use-the-iskindof-function"></a>使用 IsKindOf 函数

1. 确保类具有运行时类支持。 也就是说，该类必须直接或间接派生 `CObject` ，并使用在**DECLARE****DYNAMIC** `IMPLEMENT_DYNAMIC` `DECLARE_DYNCREATE` `IMPLEMENT_DYNCREATE` `DECLARE_SERIAL` `IMPLEMENT_SERIAL` [从 CObject 派生类一](deriving-a-class-from-cobject.md)文中介绍的 DECLARE _ DYNAMIC 和、和、或和宏。

1. 调用该类的对象的 `IsKindOf` 成员函数，并使用 `RUNTIME_CLASS` 宏生成 `CRuntimeClass` 参数，如下所示：

   [!code-cpp[NVC_MFCCObjectSample#2](codesnippet/cpp/accessing-run-time-class-information_2.h)]

   [!code-cpp[NVC_MFCCObjectSample#5](codesnippet/cpp/accessing-run-time-class-information_3.cpp)]

    > [!NOTE]
    >  如果对象是指定类的成员，或派生自指定类的类的成员，则 IsKindOf 将返回**TRUE** 。 `IsKindOf` 不支持多重继承或虚拟基类，但您可以根据需要对派生的 Microsoft 基础类使用多重继承。

运行时类信息的一种用法是在对象的动态创建中。 [动态对象创建](dynamic-object-creation.md)一文中对此过程进行了讨论。

有关序列化和运行时类信息的详细信息，请参阅文章 MFC 和[序列化](serialization-in-mfc.md)[中的文件](files-in-mfc.md)。

## <a name="see-also"></a>另请参阅

[使用 CObject](using-cobject.md)
