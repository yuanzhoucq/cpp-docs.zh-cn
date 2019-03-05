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
ms.openlocfilehash: 2e4f8685033fc7a8a2f49dafa7ef4e4e019d8989
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298823"
---
# <a name="accessing-run-time-class-information"></a>访问运行时类信息

本文说明了如何在运行时访问对象的类的相关信息。

> [!NOTE]
>  MFC 不使用[运行时类型信息](../cpp/run-time-type-information.md)(RTTI) 支持在 Visual c + + 4.0 中引入的。

如果具有派生您的类从[CObject](../mfc/reference/cobject-class.md)并用**DECLARE**_**动态**并`IMPLEMENT_DYNAMIC`，则`DECLARE_DYNCREATE`和`IMPLEMENT_DYNCREATE`，或`DECLARE_SERIAL`并`IMPLEMENT_SERIAL`宏一文中所述[从 CObject 派生类](../mfc/deriving-a-class-from-cobject.md)，则`CObject`类具有在运行时确定对象的具体类的功能。

在需要函数参数的其他类型检查时，以及在必须基于对象的类编写特殊用途的代码时，此功能非常有用。 但是，通常建议不要使用此做法，因为它会复制虚函数的功能。


  `CObject` 成员函数 `IsKindOf` 可用于确定某个特定对象是否属于某个指定类或者是否派生自某个特定类。 
  `IsKindOf` 的自变量是一个 `CRuntimeClass` 对象，您可以将 `RUNTIME_CLASS` 宏与类名一起使用来获取此对象。

### <a name="to-use-the-runtimeclass-macro"></a>使用 RUNTIME_CLASS 宏

1. 将 `RUNTIME_CLASS` 与类名一起使用，如此处为 `CObject` 类所示的：

   [!code-cpp[NVC_MFCCObjectSample#4](../mfc/codesnippet/cpp/accessing-run-time-class-information_1.cpp)]

您很少需要直接访问运行时类对象。 更常见的用法是将运行时类对象传递给 `IsKindOf` 函数，如下面的过程中所示。 
  `IsKindOf` 函数测试一个对象来确定它是否属于某个特定类。

#### <a name="to-use-the-iskindof-function"></a>使用 IsKindOf 函数

1. 确保类具有运行时类支持。 它是派生的类必须具有已直接或间接从`CObject`并用**DECLARE**_**动态**并`IMPLEMENT_DYNAMIC`，则`DECLARE_DYNCREATE`和`IMPLEMENT_DYNCREATE`，或`DECLARE_SERIAL`并`IMPLEMENT_SERIAL`宏一文中所述[从 CObject 派生类](../mfc/deriving-a-class-from-cobject.md)。

1. 调用该类的对象的 `IsKindOf` 成员函数，并使用 `RUNTIME_CLASS` 宏生成 `CRuntimeClass` 参数，如下所示：

   [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/accessing-run-time-class-information_2.h)]

   [!code-cpp[NVC_MFCCObjectSample#5](../mfc/codesnippet/cpp/accessing-run-time-class-information_3.cpp)]

    > [!NOTE]
    >  则 IsKindOf 将返回 **，则返回 TRUE**如果对象是指定类或派生自指定类的类的成员。 `IsKindOf` 不支持多重继承或虚拟基类，但您可以根据需要对派生的 Microsoft 基础类使用多重继承。

运行时类信息的一种用法是在对象的动态创建中。 在文章中讨论此过程[动态对象创建](../mfc/dynamic-object-creation.md)。

有关更多详细信息的序列化和运行时类信息，请参阅文章[MFC 中的文件](../mfc/files-in-mfc.md)并[序列化](../mfc/serialization-in-mfc.md)。

## <a name="see-also"></a>请参阅

[使用 CObject](../mfc/using-cobject.md)
