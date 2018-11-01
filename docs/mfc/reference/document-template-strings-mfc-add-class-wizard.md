---
title: “MFC 添加类向导”的文档模板字符串
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.mfc.simple.doctemp
helpviewer_keywords:
- MFC Add Class Wizard, document control strings
ms.assetid: 14e1c834-5e79-4dbd-811f-ec8f0a9cdcb2
ms.openlocfilehash: a5664a539af351051f9ae3642c089e51b54bc8cd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662418"
---
# <a name="document-template-strings-mfc-add-class-wizard"></a>“MFC 添加类向导”的文档模板字符串

在向导的此页是仅适用于满足以下条件的类：

- MFC 项目支持的文档/视图体系结构。

- 新的类的基类是[CFormView](../../mfc/reference/cformview-class.md)。

- 复选框**生成 DocTemplate 资源**检查**名称**一部分[MFC 类向导](../../mfc/reference/mfc-add-class-wizard.md)。

该向导提供以下值，以使用窗体视图的设计、 管理和本地化帮助的默认值。 由于大多数文档模板字符串是可见且由窗体的用户，它们被本地化为**资源语言**所示[应用程序类型](../../mfc/reference/application-type-mfc-application-wizard.md)MFC 应用程序向导页创建项目时。

> [!NOTE]
>  该向导不提供自动打印支持类派生自`CFormView`。

请参阅[文档模板和文档/视图创建过程](../../mfc/document-templates-and-the-document-view-creation-process.md)有关详细信息。

## <a name="nonlocalized-strings"></a>非本地化的字符串

适用于创建用户文档的应用程序。 用户可以打开和保存文档的详细信息轻松如果文档类型具有文件扩展名和文件类型 id。 这些项没有本地化，因为系统，而不是由用户使用它们。

- **文件扩展名**

   设置与此窗体应用程序的文档类型关联的文件扩展名。 文件扩展默认的基于类名称。 例如，如果新的 MFC 类命名为`CWidget`，默认情况下，文件扩展名是。 wid. 文件筛选器中使用的文件扩展名并**开放**并**另存为**对话框。

   如果更改文件扩展名，更改都反映在**筛选器名称**框。

   > [!NOTE]
   > 如果更改默认的文件扩展名，不包括句点。

- **文件类型 ID**

   默认设置为您的文档类型系统注册表中。

## <a name="localized-strings"></a>本地化的字符串

生成与窗体和读取并使用应用程序的用户，因此已本地化字符串的文档相关联的字符串。

- **文档类型名称**

   标识的文档可以在其下分组的应用程序的文档的类型。 默认情况下，它基于类的名称。 例如，如果名为新的 MFC 类**CWidget**，默认情况下，文档类型名称是小组件。 更改默认值不会更改此对话框中的任何其他选项。

- **筛选器名称**

   设置用户可以指示查找指定的文件类型的文件的名称。 此选项才可用**类型的文件**并**另存为类型**标准的 Windows 中的选项**打开**并**另存为**对话框。 默认情况下，名称基于项目名称加上扩展名的文件所示**文件扩展名**。 例如，如果你的项目名为小组件，并且文件扩展名为.wid，**筛选器名称**默认情况下是小组件文件 (*.wid)。

- **文件新的短名称**

   设置名称出现在标准 Windows**新建**对话框中，如果项目有多个文档模板。 如果你的应用程序[自动化服务器](../../mfc/automation-servers.md)，此名称用作您的自动化对象的短名称。 默认情况下，此名称基于类名称。

- **文件类型长名称**

   在系统注册表中设置的文件类型名称。 如果应用程序是自动化服务器，则此名称用作您的自动化对象的长名称。 默认情况下，此名称基于类名加上。文档。 例如，如果类名为`CWidget`，则**文件类型长名称**是小组件文档。

- **文档类**

   指示项目的文档类。 默认情况下，此类是主应用程序的文档类，如下所示[查看生成的类](../../mfc/reference/generated-classes-mfc-application-wizard.md)MFC 应用程序向导的页。 如果已在项目中添加其他文档类，可以从列表中，选择另一个文档类。

## <a name="see-also"></a>请参阅

[MFC 添加类向导](../../mfc/reference/mfc-add-class-wizard.md)<br/>
[MFC 类](../../mfc/reference/adding-an-mfc-class.md)<br/>
[添加类](../../ide/adding-a-class-visual-cpp.md)
