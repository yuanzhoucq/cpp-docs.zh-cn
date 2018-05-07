---
title: 编辑 COM 接口 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.com.editing.interfaces
dev_langs:
- C++
helpviewer_keywords:
- methods [C++], adding to COM interfaces
- COM interfaces, editing
- properties [C++], adding to COM interfaces
ms.assetid: 6c2909e0-af2d-4a37-bb39-ed372e6129cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd7a61593a1024c00c0fd0de6bd62ff3ee9323b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="editing-a-com-interface"></a>编辑 COM 接口
通过使用类视图快捷方式菜单中的命令，可以在 Visual c + + 项目中定义新的方法和属性的 COM 接口。 此外，在工具箱中，可以定义用于 ActiveX 控件的事件。  
  
 对于 ATL 和 MFC 的基于 COM 的对象类，你可以编辑在同时编辑接口的类实现。  
  
> [!NOTE]
>  接口的已定义外部**添加类**对话框中，Visual c + + 将方法或属性添加到.idl 文件中，并将存根 （stub） 添加到实现类的方法，即使这些接口手动添加。  
  
 以下三个向导帮助你自定义现有的接口。 它们是可从类视图：  
  
|向导|项目类型|  
|------------|------------------|  
|[添加属性向导](../ide/names-add-property-wizard.md)|ATL 或 MFC 项目支持 atl。 右键单击你想要添加的属性的接口。<br /><br /> Visual c + + 检测到的项目类型，并相应地修改添加属性向导中的选项：<br /><br /> -对于使用创建的项目中的调度接口[MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)，调用添加属性向导提供到 MFC 的特定选项。<br />-对于 MFC ActiveX 控件接口，添加属性向导提供常用方法和属性，可以使用所述，也可以为您的控件自定义的列表。<br />-对于所有其他接口，添加属性向导提供在大多数情况下可用的选项。|  
|[添加方法向导](../ide/add-method-wizard.md)|ATL 或 MFC 项目支持 atl。 右键单击你想要将方法添加的接口。<br /><br /> Visual c + + 检测到的项目类型，并相应地修改添加方法向导中的选项：<br /><br /> -对于使用创建的项目中的调度接口[MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)，调用添加方法向导提供到 MFC 的特定选项。<br />-对于 MFC ActiveX 控件接口添加方法向导提供常用方法和属性，可以使用所述，也可以为您的控件自定义的列表。<br />-对于所有其他接口，**添加方法**向导提供了在大多数情况下可用的选项。|  
  
 此外，你可以实现新接口对 COM 控件通过右键单击类视图中的对象的控件类并单击[实现接口](../ide/implement-interface-wizard.md)。  
  
## <a name="see-also"></a>请参阅  
 [使用资源文件](../windows/working-with-resource-files.md)   
 [用代码向导添加功能](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Visual C++ 项目类型](../ide/visual-cpp-project-types.md)