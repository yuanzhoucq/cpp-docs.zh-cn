---
title: 向单个文档添加多个视图
ms.date: 11/04/2016
helpviewer_keywords:
- multiple views [MFC], SDI applications
- documents [MFC], multiple views
- single document interface (SDI), adding views
- views [MFC], SDI applications
ms.assetid: 86d0c134-01d5-429c-b672-36cfb956dc01
ms.openlocfilehash: 593c59c73b58b4364c9d652ce8eb415c17af496c
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58767582"
---
# <a name="adding-multiple-views-to-a-single-document"></a>向单个文档添加多个视图

在使用 Microsoft 基础类 (MFC) 库创建一个单文档界面 (SDI) 应用程序，每个文档类型都与单个视图类型关联。 在某些情况下，最好的功能切换与新视图的当前视图的文档。

> [!TIP]
>  有关实现单个文档的多个视图的其他过程，请参阅[CDocument::AddView](../mfc/reference/cdocument-class.md#addview)并[收集](../overview/visual-cpp-samples.md)MFC 示例。

您可以实现此功能添加一个新的`CView`-派生的类和动态切换视图，向现有的 MFC 应用程序的其他代码。

步骤如下所示：

- [修改现有的应用程序类](#vcconmodifyexistingapplicationa1)

- [创建和修改新的视图类](#vcconnewviewclassa2)

- [创建并附加新视图](#vcconattachnewviewa3)

- [实现切换函数](#vcconswitchingfunctiona4)

- [添加用于将视图切换的支持](#vcconswitchingtheviewa5)

此主题的其余部分的假设条件如下：

- 名称`CWinApp`的派生的对象是`CMyWinApp`，并`CMyWinApp`是声明和定义中*MYWINAPP。H*和*MYWINAPP。CPP*。

- `CNewView` 是的新名称`CView`的派生的对象，并`CNewView`是声明和定义中*NEWVIEW。H*和*NEWVIEW。CPP*。

##  <a name="vcconmodifyexistingapplicationa1"></a> 修改现有的应用程序类

应用程序视图之间切换，您需要通过添加成员变量来存储视图和方法以将其切换来修改应用程序类。

将以下代码添加到声明`CMyWinApp`在*MYWINAPP。H*:

[!code-cpp[NVC_MFCDocViewSDI#1](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_1.h)]

新成员变量`m_pOldView`和`m_pNewView`，指向当前视图和新创建的一个。 新方法 (`SwitchView`) 切换视图时用户请求。 在本主题后面讨论的方法的正文[实现切换函数](#vcconswitchingfunctiona4)。

应用程序类的上次修改需要包括新的头文件，用于定义 Windows 消息 (**WM_INITIALUPDATE**) 交换函数中使用。

插入以下行中的 include 部分*MYWINAPP。CPP*:

[!code-cpp[NVC_MFCDocViewSDI#2](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_2.cpp)]

保存所做的更改并继续下一步。

##  <a name="vcconnewviewclassa2"></a> 创建和修改新的视图类

创建新的视图类可轻松使用**的新类**类视图中的可用命令。 此类的唯一要求是，它派生`CView`。 将此新类添加到应用程序。 将新类添加到项目的特定信息，请参阅[添加类](../ide/adding-a-class-visual-cpp.md)。

一旦类添加到项目后，您需要更改某些视图类成员的可访问性。

修改*NEWVIEW。H*通过更改从访问说明符**受保护**到**公共**构造函数和析构函数。 这样，此类来创建和销毁动态并修改视图外观之前可见。

保存所做的更改并继续下一步。

##  <a name="vcconattachnewviewa3"></a> 创建并附加新视图

若要创建并附加新的视图，您需要修改`InitInstance`函数的应用程序类。 修改将添加新代码： 创建新的视图对象，然后初始化这两个`m_pOldView`和`m_pNewView`与两个现有的视图对象。

因为在创建新视图`InitInstance`函数，该应用程序的生存期内保留这两个新的和现有视图。 但是，应用程序可以轻松地动态创建新视图。

在调用后，插入此代码`ProcessShellCommand`:

[!code-cpp[NVC_MFCDocViewSDI#3](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_3.cpp)]

保存所做的更改并继续下一步。

##  <a name="vcconswitchingfunctiona4"></a> 实现切换函数

在上一步骤中，您添加了创建并初始化新的视图对象的代码。 最后一个主要部分是实现的交换方法`SwitchView`。

在应用程序类的实现文件末尾 (*MYWINAPP。CPP*)，添加以下方法定义：

[!code-cpp[NVC_MFCDocViewSDI#4](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_4.cpp)]

保存所做的更改并继续下一步。

##  <a name="vcconswitchingtheviewa5"></a> 添加用于将视图切换的支持

最后一步涉及到将调用的代码添加`SwitchView`方法时，应用程序需要视图之间进行切换。 这可以通过多种方式完成： 通过添加用户选择一个新菜单项或满足某些条件时在内部切换视图。

添加新菜单项和命令处理程序函数的详细信息，请参阅[命令和控件通知处理程序](../mfc/handlers-for-commands-and-control-notifications.md)。

## <a name="see-also"></a>请参阅

[文档/视图体系结构](../mfc/document-view-architecture.md)
