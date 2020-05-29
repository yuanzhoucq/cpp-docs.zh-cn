---
title: 文档视图体系结构的替代方法
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], applications without
- CDocument class [MFC], space requirements
- views [MFC], applications without
ms.assetid: 2c22f352-a137-45ce-9971-c142173496fb
ms.openlocfilehash: 41af30d25d7ddb9e2bdbb7a0f7b86cb741ae1048
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370799"
---
# <a name="alternatives-to-the-documentview-architecture"></a>文档/视图结构的替换选项

MFC 应用程序通常使用文档/视图体系结构来管理信息、文件格式和数据对用户的可视表示形式。 对于大多数桌面应用程序，文档/视图结构是适当和有效的应用程序体系结构。 这种体系结构将数据与视图分离，大多数情况下，可简化应用程序并减少冗余代码。

但是，文档/视图体系结构对于某些情况是不合适的。 请考虑下列示例：

- 如果要移植用 C 编写的 Windows 应用程序，则可能需要先完成移植，然后在向应用程序添加文档/视图支持。

- 如果您编写某个轻量级实用工具，则可能会发现不使用文档/视图体系结构也可进行此操作。

- 如果原始代码已将数据管理与数据视图混合，则不值得将代码移到文档/视图模型，因为你必须将两者分开。 您可能更愿意将代码保留原样。

要创建不使用文档/视图体系结构的应用程序，请清除 MFC 应用程序向导步骤 1 中**的文档/视图体系结构支持**复选框。 有关详细信息，请参阅[MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)。

> [!NOTE]
> MFC 应用程序向导生成的基于对话框的应用程序不使用文档/视图体系结构，因此，如果选择对话框应用程序类型，则禁用 **"文档/视图体系结构"支持**复选框。

Visual C++ 向导以及源编辑器和对话框编辑器与生成的应用程序一起工作，就像与其他任何向导生成的应用程序一起工作一样。 应用程序可以支持工具栏、滚动条和状态栏，并且具有 **"关注"** 框。 您的应用程序将不注册任何文档模板，且不包含文档类。

请注意，生成的应用程序具有从 派生的`CChildView``CWnd`视图类。 MFC 创建视图类的一个实例并将其放置在您的应用程序创建的框架窗口中。 MFC 仍将强制使用视图窗口，因为它简化了应用程序内容的定位和管理。 你可以将绘制代码添加到此类的 `OnPaint` 成员中。 你的代码应将滚动条添加到视图而不是框架中。

由于 MFC 提供的文档/视图体系结构负责实现应用程序的许多基本功能，因此，如果项目中缺失该体系结构，则意味着您负责实现应用程序的许多重要功能：

- 如 MFC 应用程序向导提供，应用程序的菜单仅包含 **"文件**"菜单上的 **"新建**"和 **"退出**"命令。 （New**New**命令仅支持 MDI 应用程序，不支持没有文档/视图支持的 SDI 应用程序。生成的菜单资源将不支持 MRU（最近使用）列表。

- 您必须为应用程序将支持的任何命令添加处理程序函数和实现，包括"**在文件**"菜单中**打开**和**保存**。 MFC 通常会提供代码以支持这些功能，但是，此支持与文档/视图体系结构紧密相连。

- 应用程序的工具栏（如果您请求一个）将会最小化。

强烈建议您使用 MFC 应用程序向导创建应用程序，而不使用文档/视图体系结构，因为该向导可以保证正确的 MFC 体系结构。 但是，如果必须避免使用此向导，这里有几种方法可以跳过代码中的文档/视图体系结构：

- 如上面建议的，将文档视为未使用的附加物并在视图类中实现数据管理代码。 文档的开销相对较低。 单个[CDocument](../mfc/reference/cdocument-class.md)对象本身会产生少量开销，再加上`CDocument`基本类[CCmdTarget](../mfc/reference/ccmdtarget-class.md)和[CObject](../mfc/reference/cobject-class.md)的少量开销。 后面两个类都很小。

   在`CDocument`中声明 ：

  - 两个 `CString` 对象。

  - 三**个BOOL。**

  - 一个 `CDocTemplate` 指针。

  - 一个 `CPtrList` 对象，该对象包含文档视图的列表。

  此外，文档需要一定时间来创建文档对象、视图对象、框架窗口和文档模板对象。

- 将文档和视图视为未使用的附加物。 将数据管理和绘图代码放置在框架窗口而不是视图中。 此方法更接近 C 语言编程模型。

- 重写创建文档和视图的 MFC 框架部分，以便不再需要创建它们。 文档创建过程将以对 `CWinApp::AddDocTemplate` 的调用开始。 从应用程序类的 `InitInstance` 成员函数中消除该调用，而在 `InitInstance` 中创建一个框架窗口。 将数据管理代码放置在框架窗口类中。 文档/视图创建过程在[文档/视图创建](../mfc/document-view-creation.md)中进行了说明。 这种方法需要更多的工作并要求更深入地了解框架，但它使您完全避免了文档/视图开销。

一文[：使用无文档和视图的数据库类](../data/mfc-using-database-classes-without-documents-and-views.md)提供了数据库应用程序上下文中文档/视图替代方案的更具体示例。

## <a name="see-also"></a>另请参阅

[文档/视图体系结构](../mfc/document-view-architecture.md)
