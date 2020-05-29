---
title: 向单个文档添加多个视图
ms.date: 11/04/2016
helpviewer_keywords:
- multiple views [MFC], SDI applications
- documents [MFC], multiple views
- single document interface (SDI), adding views
- views [MFC], SDI applications
ms.assetid: 86d0c134-01d5-429c-b672-36cfb956dc01
ms.openlocfilehash: 4fa39a4d9369c84d2cffdaeff28dc9cb2f966b31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370856"
---
# <a name="adding-multiple-views-to-a-single-document"></a>向单个文档添加多个视图

在与 Microsoft 基础类 （MFC） 库创建的单文档接口 （SDI） 应用程序中，每个文档类型都与单个视图类型相关联。 在某些情况下，最好能够将文档的当前视图与新视图切换。

> [!TIP]
> 有关为单个文档实现多个视图的其他过程，请参阅[CDocument：AddView](../mfc/reference/cdocument-class.md#addview)和[COLLECT](../overview/visual-cpp-samples.md) MFC 示例。

您可以通过添加新`CView`派生类和其他代码来动态将视图切换到现有的 MFC 应用程序来实现此功能。

步骤如下：

- [修改现有应用程序类](#vcconmodifyexistingapplicationa1)

- [创建和修改新视图类](#vcconnewviewclassa2)

- [创建并附加新视图](#vcconattachnewviewa3)

- [实现切换功能](#vcconswitchingfunctiona4)

- [添加对切换视图的支持](#vcconswitchingtheviewa5)

本主题的其余部分假定以下内容：

- `CWinApp`派生对象的名称为`CMyWinApp`，并在`CMyWinApp`MYWINAPP 中声明和定义 *。H*和*MYWINAPP。CPP*.

- `CNewView`是新`CView`派生对象的名称，`CNewView`并在*NEWVIEW 中声明和定义。H*和*NEWVIEW。CPP*.

## <a name="modify-the-existing-application-class"></a><a name="vcconmodifyexistingapplicationa1"></a>修改现有应用程序类

要使应用程序在视图之间切换，您需要通过添加成员变量来存储视图和切换它们的方法来修改应用程序类。

将以下代码添加到`CMyWinApp`*MYWINAPP 中的声明。H*：

[!code-cpp[NVC_MFCDocViewSDI#1](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_1.h)]

新成员变量 和`m_pOldView``m_pNewView`指向当前视图和新创建的视图。 当用户请求时，`SwitchView`新方法 （ ） 会切换视图。 该方法的主体在稍后的"[实现切换函数"](#vcconswitchingfunctiona4)中讨论了本主题。

对应用程序类的最后一次修改需要包括一个新的标头文件，该文件定义在切换函数中使用的 Windows 消息 **（WM_INITIALUPDATE**）。

在 MYWINAPP 的包含部分中插入以下行 *。CPP*：

[!code-cpp[NVC_MFCDocViewSDI#2](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_2.cpp)]

保存更改并继续下一步。

## <a name="create-and-modify-the-new-view-class"></a><a name="vcconnewviewclassa2"></a>创建和修改新视图类

通过使用类视图中可用的**New Class**命令，创建新视图类变得容易。 此类的唯一要求是它派生自`CView`。 将此新类添加到应用程序。 有关向项目添加新类的特定信息，请参阅[添加类](../ide/adding-a-class-visual-cpp.md)。

将类添加到项目后，需要更改某些视图类成员的可访问性。

修改*新视图。H*通过将访问指定器从**保护**更改为**公共**构造函数和析构函数。 这允许动态创建和销毁类，并在视图可见之前对其进行修改。

保存更改并继续下一步。

## <a name="create-and-attach-the-new-view"></a><a name="vcconattachnewviewa3"></a>创建并附加新视图

要创建和附加新视图，需要修改应用程序类的`InitInstance`函数。 修改添加了新代码，该代码创建新的视图对象，然后初始化两个`m_pOldView`现有`m_pNewView`视图对象。

由于新视图是在函数中创建的，`InitInstance`因此新视图和现有视图都会在应用程序的生存期内保留。 但是，应用程序同样可以轻松地动态创建新视图。

调用 后插入此代码： `ProcessShellCommand`

[!code-cpp[NVC_MFCDocViewSDI#3](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_3.cpp)]

保存更改并继续下一步。

## <a name="implement-the-switching-function"></a><a name="vcconswitchingfunctiona4"></a>实现切换功能

在上一步中，您添加了创建和初始化新视图对象的代码。 最后一个主要部分是实现交换方法。 `SwitchView`

在应用程序类 （ MYWINAPP） 的实现文件的末尾 *。CPP*），添加以下方法定义：

[!code-cpp[NVC_MFCDocViewSDI#4](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_4.cpp)]

保存更改并继续下一步。

## <a name="add-support-for-switching-the-view"></a><a name="vcconswitchingtheviewa5"></a>添加对切换视图的支持

最后一步是在应用程序需要在视图之间切换`SwitchView`时添加调用方法的代码。 这可以通过多种方式完成：通过添加新菜单项供用户选择，或在满足某些条件时在内部切换视图。

有关添加新菜单项和命令处理程序函数的详细信息，请参阅[命令和控制通知的处理程序](../mfc/handlers-for-commands-and-control-notifications.md)。

## <a name="see-also"></a>另请参阅

[文档/视图体系结构](../mfc/document-view-architecture.md)
