---
title: 文档模板字符串，MFC 应用程序向导 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.exe.doctemp
dev_langs:
- C++
helpviewer_keywords:
- MFC Application Wizard, document template strings
ms.assetid: 8109f662-3182-4682-977a-2503321c678a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7d6039459eed097af5e927c4bd2f30d3e7c3c4bc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373535"
---
# <a name="document-template-strings-mfc-application-wizard"></a>MFC 应用程序向导的文档模板字符串
在 MFC 应用程序向导的此页中，提供或优化以下选项来帮助进行文档管理和本地化。 文档模板字符串是可用于应用程序包括**文档/视图体系结构支持**中[应用程序类型](../../mfc/reference/application-type-mfc-application-wizard.md)。 它们不能对话框。 由于大多数文档模板字符串是可见且由应用程序的用户，它们已本地化到**资源语言**中所示**应用程序类型**向导页。  
  
 **非本地化的字符串**  
 适用于应用程序创建用户文档。 用户可以打开、 打印和保存文档的详细信息轻松如果提供了文件扩展名的文件和文件类型 id。 这些项未本地化，因为系统中，而不是由用户使用它们。  
  
|选项|描述|  
|------------|-----------------|  
|**文件扩展名**|设置与使用应用程序时，用户将保存的文档关联的文件扩展名。 例如，如果你的项目名为小组件，你无法将文件扩展名.wgt。 （当你输入的文件扩展名时，请不包括期。）<br /><br /> 如果你提供的文件扩展名，资源管理器不必启动你的应用程序时用户将文档图标放置在一个打印机图标可以打印应用程序的文档。<br /><br /> 如果您不指定了扩展名，用户必须指定文件扩展名保存文件时。 向导不提供的默认文件扩展名。|  
|**文件类型 ID**|默认设置为您的文档类型系统注册表中。|  
  
 **本地化的字符串**  
 生成与关联的应用程序以及文档读取和使用由应用程序的用户，因此字符串被本地化的字符串。  
  
|选项|描述|  
|------------|-----------------|  
|**语言**|指示为所有框下显示字符串的语言**本地化字符串**。 若要更改此框中的值，选择适当的语言下**资源语言**中[应用程序类型](../../mfc/reference/application-type-mfc-application-wizard.md)MFC 应用程序向导页。|  
|**主框架标题**|设置在主应用程序框架的顶部显示的文本。 默认情况下，项目名称。|  
|**文档类型名称**|标识可以在其下分组应用程序的文档的文档的类型。 默认情况下，项目名称。 更改默认值不会更改在此对话框中的任何其他选项。|  
|**筛选器名称**|设置你的用户可以指示查找你的文件类型的文件的名称。 此选项才可用从**类型的文件**和**另存为类型**标准的 Windows 中的选项**打开**和**将另存为**对话框。 默认值，项目名称加上 Files 后, 跟中提供的扩展名**文件扩展名**。 例如，如果你的项目名为小组件中，文件，文件扩展名为.wgt，**筛选器名称**默认为小组件文件 (*.wgt)。|  
|**文件新的短名称**|设置显示在标准的 Windows 中的名称`New`对话框中，如果有多个新的文档模板。 如果你的应用程序[自动化服务器](../../mfc/automation-servers.md)，此名称用作您的自动化对象的短名称。 默认情况下，项目名称。|  
|**文件类型长名称**|在系统注册表中设置的文件类型名称。 如果你的应用程序自动化服务器，则此名称用作您的自动化对象的长名称。 默认情况下，项目名称加上。文档。|  
  
## <a name="see-also"></a>请参阅  
 [MFC 应用程序向导](../../mfc/reference/mfc-application-wizard.md)

