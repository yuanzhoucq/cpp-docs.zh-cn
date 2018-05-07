---
title: 添加类 （Visual c + +） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.classes.adding
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding classes
- classes [C++], creating
- classes [C++], adding
ms.assetid: c34b5f70-4e72-4faa-ba21-e2b05361c4d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 14e16d8b5c15939adb792a96a828bafd07ba4041
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="adding-a-class-visual-c"></a>添加类 (Visual C++)
若要在中添加在 Visual c + + 项目中，类**解决方案资源管理器**，右键单击项目，单击**添加**，然后单击**类**。 这将打开[添加类对话框](../ide/add-class-dialog-box.md)对话框。  
  
 当您添加一个类时，你必须指定与 MFC 或 atl。 中已存在的类不同的名称 如果指定的名称在库中已存在时，IDE 将显示一条错误消息。  
  
 如果你的项目命名约定要求您使用现有的名称，然后只需更改即可在名称中的一个或多个字母的大小写因为 c + + 是区分大小写。 例如，尽管不能将命名类`CDocument`，可将其命名`cdocument`。  
  
## <a name="what-kind-of-class-do-you-want-to-add"></a>要添加哪种类型的类？  
 在**添加类**对话框中，当你扩展**Visual c + +** 显示的已安装的模板的几个分组的左窗格中的节点。 组包括**CLR**， **ATL**， **MFC**，和**c + +**。 当你选择一个组时，该组中的可用模板的列表显示在中间窗格中。 每个模板包含的文件和所需的类的源代码。  
  
 若要生成一个新类，在中间窗格中选择一个模板，键入的名称中的类**名称**框中，然后单击**添加**。 这将打开**添加类向导**，以便你可以指定类的选项。  
  
-   有关如何创建 MFC 类的详细信息，请参阅[MFC 类](../mfc/reference/adding-an-mfc-class.md)。  
  
-   有关如何创建 ATL 类的详细信息，请参阅[ATL 简单对象](../atl/reference/adding-an-atl-simple-object.md)。  
  
> [!NOTE]
>  模板**向 MFC 添加 ATL 支持**不会创建一个类，但改为配置项目以使用 atl。 有关详细信息，请参阅[MFC 项目中的 ATL 支持](../mfc/reference/adding-atl-support-to-your-mfc-project.md)。  
  
 若要使不使用 MFC、 ATL 或 CLR 的 c + + 类，使用**c + + 类**中的模板**c + +** 组的已安装的模板。 有关详细信息，请参阅[添加泛型 c + + 类](../ide/adding-a-generic-cpp-class.md)。  
  
 提供了两种类型的基于窗体的 c + + 类。 第一个， [CFormView 类](../mfc/reference/cformview-class.md)创建的 MFC 类。 第二个创建 CLR Windows 窗体的类。  
  
## <a name="see-also"></a>请参阅  
 [创建基于窗体的 MFC 应用程序](../mfc/reference/creating-a-forms-based-mfc-application.md)   
 [添加类对话框](../ide/add-class-dialog-box.md)   
 [使用应用程序向导创建桌面项目](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)