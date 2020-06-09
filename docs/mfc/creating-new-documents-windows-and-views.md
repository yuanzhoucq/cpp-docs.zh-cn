---
title: 创建新文档、窗口和视图
ms.date: 11/19/2018
helpviewer_keywords:
- MDI [MFC], creating windows
- window objects [MFC], creating
- objects [MFC], creating document objects
- MFC default objects
- frame windows [MFC], creating
- windows [MFC], MDI
- MFC, documents
- view objects [MFC], creating
- windows [MFC], creating
- overriding, default view behavior
- views [MFC], initializing
- customizing MFC default objects
- MFC, frame windows
- MFC, views
- MDI [MFC], frame windows
- child windows [MFC], creating MDI
- view objects [MFC]
- document objects [MFC], creating
- MFC default objects [MFC], customizing
- views [MFC], overriding default behavior
- initializing views [MFC]
ms.assetid: 88aa1f5f-2078-4603-b16b-a2b4c7b4a2a3
ms.openlocfilehash: 7a714b5d7ba97c12b7134fa4890bddf5ed095c5b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620566"
---
# <a name="creating-new-documents-windows-and-views"></a>创建新文档、窗口和视图

下列各图概述了文档、视图和框架窗口的创建过程。 其他关注参与对象的文章将提供更多详细信息。

在完成此过程之后，协同对象将存在并且将存储指向彼此的指针。 下列各图显示了对象的创建顺序。 您可以遵循各图之间的顺序。

![用于创建文档的序列](../mfc/media/vc387l1.gif "用于创建文档的序列") <br/>
文档创建顺序

![框架窗口创建序列](../mfc/media/vc387l2.png "框架窗口创建序列") <br/>
框架窗口创建顺序

![用于创建视图的序列](../mfc/media/vc387l3.gif "用于创建视图的序列") <br/>
视图创建顺序

有关框架如何初始化新文档、视图和框架窗口对象的信息，请参阅 MFC 库参考中的类[CDocument](reference/cdocument-class.md)、 [CView](reference/cview-class.md)、 [CFrameWnd](reference/cframewnd-class.md)、 [CMDIFrameWnd](reference/cmdiframewnd-class.md)和[CMDIChildWnd](reference/cmdichildwnd-class.md) 。 另请参阅[技术说明 22](tn022-standard-commands-implementation.md)，其中进一步说明了在框架的标准命令（对于 "**文件**" 菜单上的 "**新建**" 和 "**打开**" 项）的讨论下的创建和初始化过程。

## <a name="initializing-your-own-additions-to-these-classes"></a><a name="_core_initializing_your_own_additions_to_these_classes"></a>初始化对这些类的添加

上面各图还建议了您可重写成员函数以初始化应用程序对象的位置。 视图类中 `OnInitialUpdate` 的重写是最适合初始化视图的位置。 `OnInitialUpdate` 调用将在创建框架窗口并且框架窗口中的视图附加到其文档之后立即出现。 例如，如果您的视图是滚动视图（派生自 `CScrollView` 而不是 `CView`），则您应基于 `OnInitialUpdate` 重写中的文档大小设置视图大小。 （ [CScrollView](reference/cscrollview-class.md)类的说明中描述了此过程。）您可以重写 `CDocument` 成员函数 `OnNewDocument` 并 `OnOpenDocument` 提供文档的应用程序特定的初始化。 通常，您必须重写二者，因为文档可通过两种方式创建。

在大多数情况下，您的重写应调用基类版本。 有关详细信息，请参阅 MFC 库参考中的[CDocument](reference/cdocument-class.md)、 [CView](reference/cview-class.md)、 [CFrameWnd](reference/cframewnd-class.md)和[CWinApp](reference/cwinapp-class.md)类的命名成员函数。

## <a name="see-also"></a>另请参阅

[文档模板和文档/视图创建过程](document-templates-and-the-document-view-creation-process.md)<br/>
[文档模板创建](document-template-creation.md)<br/>
[文档/视图创建](document-view-creation.md)<br/>
[MFC 对象之间的关系](relationships-among-mfc-objects.md)
