---
title: 添加类 (Visual C++)
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.classes.adding
helpviewer_keywords:
- ATL projects, adding classes
- classes [C++], creating
- classes [C++], adding
ms.assetid: c34b5f70-4e72-4faa-ba21-e2b05361c4d9
ms.openlocfilehash: 8cdc8dcc4241acb805255b6a28f1518e39f2bb75
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429375"
---
# <a name="adding-a-class-visual-c"></a>添加类 (Visual C++)

要在 Visual C++ 项目中添加类，请在“解决方案资源管理器”中，右键单击该项目，单击“添加”，然后单击“类”。 这将打开[“添加类”对话框](../ide/add-class-dialog-box.md)。

添加类时，指定的名称必须与 MFC 或 ATL 中已有的类的名称不同。 如果指定了 MFC 或 ATL 库中已存在的名称，IDE 将显示一条错误消息。

如果项目命名约定要求使用现有名称，则只需更改名称中一个或多个字母的大小写，因为 C++ 区分大小写。 例如，无法将类命名为 `CDocument`，但可将其命名为 `cdocument`。

## <a name="what-kind-of-class-do-you-want-to-add"></a>要添加哪种类型的类？

在“添加类”对话框中，展开左窗格中的“Visual C++”节点时，将显示几个组，列出已安装的模板。 这些组包括 CLR、ATL、MFC 和 C++。 选择组时，中间的窗格将显示该组中可用模板的列表。 每个模板都包含类所需的文件和源代码。

要生成新类，请在中间的窗格选择一个模板，在“名称”框中键入类的名称，然后单击“添加”。 这会打开“添加类向导”，可在此指定该类的选项。

- 若要详细了解如何创建 MFC 类，请参阅 [MFC 类](../mfc/reference/adding-an-mfc-class.md)。

- 若要详细了解如何创建 ATL 类，请参阅 [ATL 简单对象](../atl/reference/adding-an-atl-simple-object.md)。

> [!NOTE]
>  “将 ATL 支持添加到 MFC”模板不会创建类，而是将项目配置为使用 ATL。 有关详细信息，请参阅 [MFC 项目中的 ATL 支持](../mfc/reference/adding-atl-support-to-your-mfc-project.md)。

要创建不使用 MFC、ATL 和 CLR 的 C++ 类，请使用已安装模板的“C++”组中的“C++ 类”模板。 有关详细信息，请参阅[添加泛型 C++ 类](../ide/adding-a-generic-cpp-class.md)。

有两种基于表单的 C++ 类可用。 第一种是 [CFormView 类](../mfc/reference/cformview-class.md)，可创建 MFC 类。 第二种创建 CLR Windows 窗体类。

## <a name="see-also"></a>请参阅

[创建基于窗体的 MFC 应用程序](../mfc/reference/creating-a-forms-based-mfc-application.md)<br>
[“添加类”对话框](../ide/add-class-dialog-box.md)<br>
[使用应用程序向导创建桌面项目](../ide/creating-desktop-projects-by-using-application-wizards.md)<br>
[用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)