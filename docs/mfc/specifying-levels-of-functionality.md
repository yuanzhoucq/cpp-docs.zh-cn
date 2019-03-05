---
title: 指定功能级别
ms.date: 11/06/2018
helpviewer_keywords:
- CObject class [MFC], adding functionality to derived classes
- runtime [MFC], class information
- serialization [MFC], Cobject
- dynamic creation support
- levels [MFC], functionality in CObject
- run-time class [MFC], information support
- levels [MFC]
ms.assetid: 562669ba-c858-4f66-b5f1-b3beeea4f486
ms.openlocfilehash: c3b4ecb38054748f36d75ca43e32d6447d3d2428
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299903"
---
# <a name="specifying-levels-of-functionality"></a>指定功能级别

本文介绍如何将添加以下级别的功能提供给你[CObject](../mfc/reference/cobject-class.md)-派生的类：

- 运行时类信息

- 动态创建支持

- 序列化支持

有关的一般描述`CObject`功能，请参阅文章[从 CObject 派生类](../mfc/deriving-a-class-from-cobject.md)。

## <a name="to-add-run-time-class-information"></a>若要添加运行时类信息

1. 从类派生`CObject`，如中所述[从 CObject 派生类](../mfc/deriving-a-class-from-cobject.md)一文。

1. 在类声明中，使用 DECLARE_DYNAMIC 宏，如下所示：

   [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/specifying-levels-of-functionality_1.h)]

1. 在实现文件中使用 IMPLEMENT_DYNAMIC 宏 (。CPP) 的类。 此宏将作为自变量类和其基类的名称，如下所示：

   [!code-cpp[NVC_MFCCObjectSample#3](../mfc/codesnippet/cpp/specifying-levels-of-functionality_2.cpp)]

> [!NOTE]
> 始终将 IMPLEMENT_DYNAMIC 放在实现文件 (。CPP) 为您的类。 IMPLEMENT_DYNAMIC 宏在编译期间应仅一次进行评估，并因此不应使用接口文件中 (。H） 中可有可能包括在多个文件。

## <a name="to-add-dynamic-creation-support"></a>若要添加动态创建的支持

1. 派生您的类从`CObject`。

1. 在类声明中使用 DECLARE_DYNCREATE 宏。

1. 定义构造函数不带任何参数 （默认构造函数）。

1. 类实现文件中使用 IMPLEMENT_DYNCREATE 宏。

## <a name="to-add-serialization-support"></a>若要添加的序列化支持

1. 派生您的类从`CObject`。

1. 重写`Serialize`成员函数。

   > [!NOTE]
   > 如果调用`Serialize`直接，也就是说，不要序列化通过多态指针对象，省略步骤 3 至 5。

1. 在类声明中使用 DECLARE_SERIAL 宏。

1. 定义构造函数不带任何参数 （默认构造函数）。

1. 类实现文件中使用 IMPLEMENT_SERIAL 宏。

> [!NOTE]
> 指向类的对象的"多态指针"(调用它的) 或从 （举例来说，B） 派生的任何类的对象。 若要通过多态指针序列化，框架必须确定它序列化 (B)，因为它可能是派生自一些基类 (A) 任何类的对象的对象的运行时类。

有关如何从您的类派生时启用序列化的详细信息`CObject`，请参阅文章[MFC 中的文件](../mfc/files-in-mfc.md)并[序列化](../mfc/serialization-in-mfc.md)。

## <a name="see-also"></a>请参阅

[从 CObject 派生类](../mfc/deriving-a-class-from-cobject.md)
