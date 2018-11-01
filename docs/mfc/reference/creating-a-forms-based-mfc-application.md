---
title: 创建基于窗体的 MFC 应用程序
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfcforms.project
helpviewer_keywords:
- applications [MFC], forms-based
- forms-based applications [MFC]
ms.assetid: 048d2f7d-b60d-4386-ad8e-71d49af9c05e
ms.openlocfilehash: d95a5ddd5b8504bedc8136ae553b62b3ee6740f7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518594"
---
# <a name="creating-a-forms-based-mfc-application"></a>创建基于窗体的 MFC 应用程序

窗体是让用户访问和可能更改数据的控件的对话框。 您可能想要开发的应用程序用户从窗体的选择。 通常，基于窗体的应用程序允许用户访问窗体通过单击**新建**从**文件**菜单。 一个基于对话框的应用程序，其中不允许用户访问**新建**选项**文件**菜单中，也被视为基于窗体的应用程序。

单文档界面 (SDI)，基于窗体的应用程序允许一个特定的窗体以运行一次只有一个的实例。 可以通过选择新的窗体从不同的形式在同一时间运行 SDI 基于窗体的应用程序从**新建**选项**文件**菜单。

如果创建多文档界面 (MDI) 基于窗体的应用程序中，应用程序将能够支持多个实例的同一窗体。

如果具有多个顶级文档支持创建应用程序，桌面是隐式父级为文档和文档的框架并不局限于应用程序的客户端区域。 您可以打开文档，每个都有其自己的框架、 菜单和任务栏图标的多个实例。 但如果您选择，关闭单个文档的后续实例**退出**选项从**文件**初始实例，该应用程序的菜单关闭所有实例。

SDI、 MDI 和多个顶级文档应用程序是基于所有窗体，并且使用文档/视图体系结构。

根据定义，任何基于对话框的应用程序都基于窗体。 基于对话框的应用程序不使用文档/视图体系结构，因此，您必须为其他窗体管理创建和访问方法。

基于窗体的应用程序的基类是[CFormView](../../mfc/reference/cformview-class.md)。 如果你的应用程序具有数据库支持，则您还可以选择任何类都派生自`CFormView`。 一种形式是派生自任何窗口`CFormView`或从任何类都继承自`CFormView`。

即使你使用的基类，例如[CView](../../mfc/reference/cview-class.md)，你可以更高版本进行您的应用程序的基于窗体[添加 MFC 类](../../mfc/reference/adding-an-mfc-class.md)派生自`CFormView`并检查**生成 DocTemplate资源**中的复选框[MFC 类向导](../../mfc/reference/document-template-strings-mfc-add-class-wizard.md)。

一旦完成该向导时，将打开你的项目，并且选中`CFormView`(或类继承自`CFormView`) 作为基类或 Visual c + + 创建一个基于对话框的应用程序，如果打开对话框编辑器。 此时，已准备好设计第一个窗体。

### <a name="to-begin-creating-a-forms-based-mfc-executable"></a>若要开始创建一个基于窗体的 MFC 可执行文件

1. 按照中的说明[创建 MFC 应用程序](../../mfc/reference/creating-an-mfc-application.md)。

1. 在 MFC 应用程序向导[应用程序类型](../../mfc/reference/application-type-mfc-application-wizard.md)页上，选择**文档/视图体系结构支持**复选框。

1. 选择**单个文档**，**多个文档**，或**多个顶级文档**。

    > [!NOTE]
    >  如果选择了 SDI、 MDI 或多个顶级文档界面应用程序，则默认情况下，`CView`设置为应用程序的视图中的类的基类[生成的类](../../mfc/reference/generated-classes-mfc-application-wizard.md)向导页。 若要创建基于窗体的应用程序，必须选择`CFormView`作为应用程序的视图的基类。 请注意，该向导为基于窗体的应用程序提供了任何打印支持。

1. 在向导的其他页面上设置所需的任何其他项目选项。

1. 单击**完成**生成主干应用程序。

有关详细信息，请参见:

- [派生的视图类](../../mfc/derived-view-classes-available-in-mfc.md)

- [文档/视图体系结构的替代方法](../../mfc/alternatives-to-the-document-view-architecture.md)

- [应用程序设计选项](../../mfc/application-design-choices.md)

## <a name="see-also"></a>请参阅

[MFC 应用程序向导](../../mfc/reference/mfc-application-wizard.md)<br/>
[窗体视图](../../mfc/form-views-mfc.md)<br/>
[创建文件资源管理器样式的 MFC 应用程序](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)<br/>
[创建 Web 浏览器样式的 MFC 应用程序](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)

