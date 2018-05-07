---
title: 向单个文档添加多个视图 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- multiple views [MFC], SDI applications
- documents [MFC], multiple views
- single document interface (SDI), adding views
- views [MFC], SDI applications
ms.assetid: 86d0c134-01d5-429c-b672-36cfb956dc01
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb40b356b5601e19c33083c7b731a1dc411de3c5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="adding-multiple-views-to-a-single-document"></a>向单个文档添加多个视图
在使用 Microsoft 基础类 (MFC) 库创建一个单文档界面 (SDI) 的应用程序的情况下，每种文档类型都与单个视图类型关联。 在某些情况下，最好切换文档与新视图的当前视图的功能。  
  
> [!TIP]
>  有关实现单个文档的多个视图的其他过程，请参阅[CDocument::AddView](../mfc/reference/cdocument-class.md#addview)和[收集](../visual-cpp-samples.md)MFC 示例。  
  
 你可以添加一个新的实现此功能`CView`-派生的类以及用于向现有的 MFC 应用程序动态切换视图的其他代码。  
  
 步骤如下所示：  
  
-   [修改现有的应用程序类](#vcconmodifyexistingapplicationa1)  
  
-   [创建和修改新的视图类](#vcconnewviewclassa2)  
  
-   [创建并附加新视图](#vcconattachnewviewa3)  
  
-   [实现切换函数](#vcconswitchingfunctiona4)  
  
-   [添加用于将视图切换的支持](#vcconswitchingtheviewa5)  
  
 此主题的其余部分假设如下：  
  
-   名称`CWinApp`-派生的对象是`CMyWinApp`，和`CMyWinApp`声明并在 MYWINAPP 中定义。H 和 MYWINAPP。CPP。  
  
-   `CNewView` 是的新名称`CView`-派生的对象，和`CNewView`是声明和定义中新建。H 和新建。CPP。  
  
##  <a name="vcconmodifyexistingapplicationa1"></a> 修改现有的应用程序类  
 对于应用程序的视图之间切换，你需要通过添加成员变量以存储视图和方法来将它们转换来修改应用程序类。  
  
 将以下代码添加到的声明`CMyWinApp`MYWINAPP 中。H:  
  
 [!code-cpp[NVC_MFCDocViewSDI#1](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_1.h)]  
  
 新成员变量，`m_pOldView`和`m_pNewView`，指向当前视图和新创建的一个。 新的方法 (`SwitchView`) 视图的用户请求之间进行切换。 稍后在本主题将讨论方法的正文[实现切换函数](#vcconswitchingfunctiona4)。  
  
 上次修改与应用程序类需要包括新的头文件，用于定义 Windows 消息 (**WM_INITIALUPDATE**)，但切换函数中使用。  
  
 在包含一部分 MYWINAPP 中插入以下行。CPP:  
  
 [!code-cpp[NVC_MFCDocViewSDI#2](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_2.cpp)]  
  
 保存所做的更改并继续下一步。  
  
##  <a name="vcconnewviewclassa2"></a> 创建和修改新的视图类  
 创建新的视图类更方便了通过使用**新类**类视图中的可用命令。 此类的唯一要求是，它派生自`CView`。 将此新类添加到应用程序。 将新类添加到项目的特定信息，请参阅[添加类](../ide/adding-a-class-visual-cpp.md)。  
  
 在已经将类添加到项目中，你需要更改某些视图类成员的可访问性。  
  
 修改新建。通过更改从访问说明符 H`protected`到**公共**对构造函数和析构函数。 这使类以创建和销毁动态，并修改视图外观之前可见。  
  
 保存所做的更改并继续下一步。  
  
##  <a name="vcconattachnewviewa3"></a> 创建并附加新视图  
 若要创建并附加新视图，你需要修改`InitInstance`应用程序类的函数。 修改将添加新的代码创建一个新的视图对象，然后初始化这两个`m_pOldView`和`m_pNewView`与两个现有视图对象。  
  
 因为在创建了新视图`InitInstance`函数，该应用程序的生存期内保留这两个新的和现有视图。 但是，应用程序可以轻松地动态创建新视图。  
  
 插入此代码的调用后`ProcessShellCommand`:  
  
 [!code-cpp[NVC_MFCDocViewSDI#3](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_3.cpp)]  
  
 保存所做的更改并继续下一步。  
  
##  <a name="vcconswitchingfunctiona4"></a> 实现切换函数  
 在上一步骤中，添加了代码创建和初始化新的视图对象。 最后一个主要一步是实现切换的方法， `SwitchView`。  
  
 在你的应用程序的实现文件末尾类 (MYWINAPP。CPP) 中，添加以下方法定义：  
  
 [!code-cpp[NVC_MFCDocViewSDI#4](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_4.cpp)]  
  
 保存所做的更改并继续下一步。  
  
##  <a name="vcconswitchingtheviewa5"></a> 添加用于将视图切换的支持  
 最后一个步骤涉及将调用的代码添加`SwitchView`方法时该应用程序需要的视图之间切换。 这可以通过多种方式完成： 通过添加用户选择一个新菜单项或满足某些条件时从内部切换视图。  
  
 添加新菜单项和命令处理程序函数的详细信息，请参阅[命令和控件通知处理程序](../mfc/handlers-for-commands-and-control-notifications.md)。  
  
## <a name="see-also"></a>请参阅  
 [文档/视图体系结构](../mfc/document-view-architecture.md)

