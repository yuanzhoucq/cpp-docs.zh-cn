---
title: 文档模板字符串 MFC 添加类向导 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.class.mfc.simple.doctemp
dev_langs:
- C++
helpviewer_keywords:
- MFC Add Class Wizard, document control strings
ms.assetid: 14e1c834-5e79-4dbd-811f-ec8f0a9cdcb2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 81b14e0c397ac9179142627bca04b647c1db96db
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="document-template-strings-mfc-add-class-wizard"></a>“MFC 添加类向导”的文档模板字符串
向导的此页是仅适用于满足以下条件类：  
  
-   MFC 项目支持的文档/视图体系结构。  
  
-   新类的基类是[CFormView](../../mfc/reference/cformview-class.md)。  
  
-   复选框**生成 DocTemplate 资源**上选中了**名称**部分[MFC 类向导](../../mfc/reference/mfc-add-class-wizard.md)。  
  
 该向导提供以下值，以帮助进行窗体视图设计、 管理和本地化的默认值。 由于大多数文档模板字符串是可见且由窗体的用户，它们已本地化到**资源语言**中所示[应用程序类型](../../mfc/reference/application-type-mfc-application-wizard.md)MFC 应用程序向导页创建项目时。  
  
> [!NOTE]
>  向导不提供自动打印支持类派生自`CFormView`。  
  
 请参阅[文档模板和文档/视图创建过程](../../mfc/document-templates-and-the-document-view-creation-process.md)有关详细信息。  
  
## <a name="nonlocalized-strings"></a>非本地化的字符串  
 适用于应用程序创建用户文档。 用户可以打开和保存文档的详细信息轻松如果文档类型具有文件扩展名的文件和文件类型 id。 这些项未本地化，因为系统中，而不是由用户使用它们。  
  
 **文件扩展名**  
 设置与此窗体应用程序的文档类型关联的文件扩展名。 基于类名称的文件扩展名默认。 例如，如果新的 MFC 类命名为**CWidget**，默认情况下，文件扩展名是。 wid. 在文件筛选器中使用的文件扩展名和**打开**和**将另存为**对话框。  
  
 如果更改文件扩展名，更改会反映在**筛选器名称**框。  
  
> [!NOTE]
>  如果更改默认文件扩展名，不包括句点。  
  
 **文件类型 ID**  
 默认设置为您的文档类型系统注册表中。  
  
## <a name="localized-strings"></a>本地化的字符串  
 生成与窗体和读取并由应用程序的用户，因此字符串被本地化文档相关联的字符串。  
  
 **文档类型名称**  
 标识可以在其下分组应用程序的文档的文档的类型。 默认情况下，它基于类的名称。 例如，如果新的 MFC 类命名为**CWidget**，默认情况下，文档类型名称就是小组件。 更改默认值不会更改在此对话框中的任何其他选项。  
  
 **筛选器名称**  
 设置用户可以指示以查找指定的文件类型的文件的名称。 此选项才可用从**类型的文件**和**另存为类型**标准的 Windows 中的选项**打开**和**将另存为**对话框。 默认情况下，该名称基于项目名称加上 Files 后, 跟扩展所示**文件扩展名**。 例如，如果你的项目名为小组件中，文件，文件扩展名为.wid，**筛选器名称**默认为小组件文件 (*.wid)。  
  
 **文件新的短名称**  
 设置显示在标准的 Windows 中的名称`New`对话框中，如果该项目包含多个文档模板。 如果你的应用程序[自动化服务器](../../mfc/automation-servers.md)，此名称用作您的自动化对象的短名称。 默认情况下，此名称基于类名称。  
  
 **文件类型长名称**  
 在系统注册表中设置的文件类型名称。 如果你的应用程序自动化服务器，则此名称用作您的自动化对象的长名称。 默认情况下，此名称基于类名加上。文档。 例如，如果类名称为**CWidget**、**文件类型长名称**是小组件文档。  
  
 **文档类**  
 指示项目的文档类。 默认情况下，此类是主应用程序的文档类，如所示[查看生成的类](../../mfc/reference/generated-classes-mfc-application-wizard.md)MFC 应用程序向导页。 如果你已在项目中添加其他文档类，可以从列表中，选择另一个文档类。  
  
## <a name="see-also"></a>请参阅  
 [MFC 添加类向导](../../mfc/reference/mfc-add-class-wizard.md)   
 [MFC 类](../../mfc/reference/adding-an-mfc-class.md)   
 [添加类](../../ide/adding-a-class-visual-cpp.md)
