---
title: "用于创建 ActiveX 控件的操作顺序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], creating
- ActiveX controls [MFC], creating
- sequence [MFC], for creating ActiveX controls
- OLE controls [MFC], MFC
- sequence [MFC]
ms.assetid: 7d868c53-a0af-4ef6-a89c-e1c03c583a53
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1e16254d7be929596d1205fa22cb5d62323d077d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="sequence-of-operations-for-creating-activex-controls"></a>用于创建 ActiveX 控件的操作顺序
下表显示你的角色和框架的角色中创建 ActiveX 控件 （以前称为 OLE 控件）。  
  
### <a name="creating-activex-controls"></a>创建 ActiveX 控件  
  
|任务|您执行的操作|框架执行的操作|  
|----------|------------|------------------------|  
|创建 ActiveX 控件框架。|运行 MFC ActiveX 控件向导以创建您的控件。 在选项页中指定您需要的选项。 选项包括在项目、 许可、 子类化，以及有关框方法的类型和控件的名称。|MFC ActiveX 控件向导创建 ActiveX 控件的文件具有基本功能，包括源文件你应用程序、 控件和属性页或页面; 例如：资源文件;一个项目文件;和其他人，所有定制的您的规范。|  
|请参阅而无需添加你自己的代码线控件和 ActiveX 控件向导提供的内容。|生成 ActiveX 控件，并使用 Internet 资源管理器对其进行测试或[TSTCON 示例](../visual-cpp-samples.md)。|正在运行的控件具有可调整大小和移动的能力。 它还具有**有关框**可以调用的方法 （如果选择）。|  
|实现控件的方法和属性。|通过添加成员函数以提供对控件的数据的公开的接口实现特定于控件的方法和属性。 添加成员变量以保留数据结构和事件处理程序用于触发事件; 当你确定。|框架已定义一个映射，以便支持控件的事件、 属性和方法，从而使你能够专注于如何实现的属性和方法。 默认属性页仅可查看和提供默认有关框方法。|  
|构造该控件的属性页。|使用 Visual c + + 资源编辑器直观地编辑控件的属性页接口：<br /><br /> -创建附加的属性页。<br />-创建并编辑位图、 图标和光标。<br /><br /> 你还可以在对话框编辑器中测试的属性页。|MFC 应用程序向导创建的默认资源文件提供了很多您需要的资源。 利用 Visual C++，您可以轻松直观地编辑现有资源和添加新资源。|  
|测试控件的事件、 方法和属性。|重新生成该控件，并使用测试容器测试您的处理程序是否正常工作。|你可以调用该控件的方法和操作其通过属性页界面或测试容器的属性。 此外，使用测试容器，以从控件触发的跟踪事件和控件的容器接收通知。|  
  
## <a name="see-also"></a>请参阅  
 [基于框架生成](../mfc/building-on-the-framework.md)   
 [用于生成 MFC 应用程序的操作顺序](../mfc/sequence-of-operations-for-building-mfc-applications.md)   
 [用于创建 OLE 应用程序的操作顺序](../mfc/sequence-of-operations-for-creating-ole-applications.md)   
 [数据库应用程序的创建操作顺序](../mfc/sequence-of-operations-for-creating-database-applications.md)

