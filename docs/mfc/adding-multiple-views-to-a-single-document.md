---
title: 向单个文档添加多个视图
ms.date: 11/04/2016
helpviewer_keywords:
- multiple views [MFC], SDI applications
- documents [MFC], multiple views
- single document interface (SDI), adding views
- views [MFC], SDI applications
ms.assetid: 86d0c134-01d5-429c-b672-36cfb956dc01
ms.openlocfilehash: 83bb7e54567319a7af4bd3d8a6bf02256fef68fb
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623359"
---
# <a name="adding-multiple-views-to-a-single-document"></a>向单个文档添加多个视图

在使用 Microsoft 基础类（MFC）库创建的单文档界面（SDI）应用程序中，每个文档类型都与一个视图类型相关联。 在某些情况下，最好能够使用新视图来切换文档的当前视图。

> [!TIP]
> 有关实现单个文档的多个视图的其他过程，请参阅[CDocument：： AddView](reference/cdocument-class.md#addview)和[收集](../overview/visual-cpp-samples.md)MFC 示例。

可以通过添加一个新的 `CView` 派生类和用于将视图动态切换到现有 MFC 应用程序的附加代码来实现此功能。

步骤如下：

- [修改现有应用程序类](#vcconmodifyexistingapplicationa1)

- [创建和修改新的视图类](#vcconnewviewclassa2)

- [创建并附加新视图](#vcconattachnewviewa3)

- [实现切换函数](#vcconswitchingfunctiona4)

- [添加对切换视图的支持](#vcconswitchingtheviewa5)

本主题的其余部分假定以下内容：

- 派生对象的名称 `CWinApp` 为 `CMyWinApp` ，并 `CMyWinApp` 在 MYWINAPP 中声明和定义 *。H*和*MYWINAPP。CPP*。

- `CNewView`是新派生对象的名称 `CView` ，并 `CNewView` 在 NEWVIEW 中声明和定义 *。H*和*NEWVIEW。CPP*。

## <a name="modify-the-existing-application-class"></a><a name="vcconmodifyexistingapplicationa1"></a>修改现有应用程序类

要使应用程序在两个视图之间切换，需要通过添加成员变量来存储视图，并使用方法来修改应用程序类。

将以下代码添加到 `CMyWinApp` MYWINAPP 中的声明 *。H*：

[!code-cpp[NVC_MFCDocViewSDI#1](codesnippet/cpp/adding-multiple-views-to-a-single-document_1.h)]

新成员变量 `m_pOldView` 和 `m_pNewView` ，指向当前视图和新创建的视图。 新方法（ `SwitchView` ）在用户请求时切换视图。 本主题后面的[实现切换函数](#vcconswitchingfunctiona4)中讨论了该方法的主体。

对应用程序类的最后修改需要包括一个新的头文件，该文件定义在切换函数中使用的 Windows 消息（**WM_INITIALUPDATE**）。

在 MYWINAPP 的 include 节中插入以下行 *。CPP*：

[!code-cpp[NVC_MFCDocViewSDI#2](codesnippet/cpp/adding-multiple-views-to-a-single-document_2.cpp)]

保存更改，然后继续下一步。

## <a name="create-and-modify-the-new-view-class"></a><a name="vcconnewviewclassa2"></a>创建和修改新的视图类

通过使用类视图提供的 "**新建类**" 命令，可以轻松创建新的视图类。 此类的唯一要求是派生自 `CView` 。 将此新类添加到应用程序。 有关将新类添加到项目的特定信息，请参阅[添加类](../ide/adding-a-class-visual-cpp.md)。

将类添加到项目后，需要更改某些视图类成员的可访问性。

修改*NEWVIEW。H* ：将访问说明符从**protected** to **public**更改为构造函数和析构函数。 这允许动态创建和销毁类，并在视图外观可见之前修改其外观。

保存更改，然后继续下一步。

## <a name="create-and-attach-the-new-view"></a><a name="vcconattachnewviewa3"></a>创建并附加新视图

若要创建并附加新视图，需要修改 `InitInstance` 应用程序类的函数。 修改将添加新的代码，用于创建新的视图对象，然后 `m_pOldView` `m_pNewView` 使用两个现有视图对象初始化和。

由于新视图是在函数内创建的，因此在 `InitInstance` 应用程序的生存期内会保留新的和现有的视图。 但是，应用程序可以轻松地动态创建新视图。

在调用后插入以下代码 `ProcessShellCommand` ：

[!code-cpp[NVC_MFCDocViewSDI#3](codesnippet/cpp/adding-multiple-views-to-a-single-document_3.cpp)]

保存更改，然后继续下一步。

## <a name="implement-the-switching-function"></a><a name="vcconswitchingfunctiona4"></a>实现切换函数

在上一步中，你添加了创建并初始化了新视图对象的代码。 最后一个主要部分是实现交换方法 `SwitchView` 。

在应用程序类的实现文件的末尾（MYWINAPP）*。CPP*）中，添加以下方法定义：

[!code-cpp[NVC_MFCDocViewSDI#4](codesnippet/cpp/adding-multiple-views-to-a-single-document_4.cpp)]

保存更改，然后继续下一步。

## <a name="add-support-for-switching-the-view"></a><a name="vcconswitchingtheviewa5"></a>添加对切换视图的支持

最后一个步骤涉及添加 `SwitchView` 在应用程序需要在视图之间切换时调用方法的代码。 可以通过以下几种方式完成此操作：在满足某些条件时，为用户添加新的菜单项以选择或切换视图。

有关添加新菜单项和命令处理程序函数的详细信息，请参阅[命令和控件通知的处理程序](handlers-for-commands-and-control-notifications.md)。

## <a name="see-also"></a>另请参阅

[文档/视图体系结构](document-view-architecture.md)
