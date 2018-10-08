---
title: 用于创建 ActiveX 控件的操作顺序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], creating
- ActiveX controls [MFC], creating
- sequence [MFC], for creating ActiveX controls
- OLE controls [MFC], MFC
- sequence [MFC]
ms.assetid: 7d868c53-a0af-4ef6-a89c-e1c03c583a53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c79a9cace0cf2eacabdba63f327f86e95959f3fb
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861468"
---
# <a name="sequence-of-operations-for-creating-activex-controls"></a>用于创建 ActiveX 控件的操作顺序

下表显示了创建 ActiveX 控件 （以前称为 OLE 控件） 你的角色和框架的角色。

### <a name="creating-activex-controls"></a>创建 ActiveX 控件

|任务|您执行的操作|框架执行的操作|
|----------|------------|------------------------|
|创建 ActiveX 控件框架。|运行 MFC ActiveX 控件向导创建您的控件。 在选项页中指定您需要的选项。 选项包括在项目、 许可、 子类化和关于中方法的类型和控件的名称。|MFC ActiveX 控件向导会创建具有基本功能，包括源代码文件为你的应用程序、 控件和属性页或页面; 例如： 对 ActiveX 控件文件资源文件;一个项目文件;和其他人，所有针对您的规范。|
|请参阅而无需将你自己的代码行添加控件和 ActiveX 控件向导提供的哪些功能。|生成 ActiveX 控件并对其进行测试与 Internet 资源管理器或[TSTCON 示例](../visual-cpp-samples.md)。|在运行控件具有可调整大小和移动功能。 它还具有**关于框**可以调用的方法 （如果选择）。|
|实现控件的方法和属性。|通过添加成员函数以提供对控件的数据的公开的接口来实现特定于控件的方法和属性。 添加成员变量以保留数据结构，并使用事件处理程序来引发事件时确定。|该框架已定义一个映射，以便支持控件的事件、 属性和方法，从而使您可以专注于如何实现的属性和方法。 默认属性页仅可查看和提供默认的关于框方法。|
|控件的属性页来构造。|使用 Visual c + + 资源编辑器以直观地编辑控件的属性页界面：<br /><br />-创建附加属性页。<br />-创建和编辑位图、 图标和光标。<br /><br /> 此外可以在对话框编辑器中测试的属性页。|MFC 应用程序向导创建的默认资源文件提供了很多您需要的资源。 利用 Visual C++，您可以轻松直观地编辑现有资源和添加新资源。|
|测试控件的事件、 方法和属性。|重新生成该控件，并使用测试容器测试您的处理程序正常工作。|您可以调用控件的方法并控制其属性通过属性页界面或测试容器。 此外，使用测试容器，以从控件触发的跟踪事件和控件的容器所收到的通知。|

## <a name="see-also"></a>请参阅

[基于框架生成](../mfc/building-on-the-framework.md)<br/>
[MFC 应用程序的构建操作顺序](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[OLE 应用程序的创建操作顺序](../mfc/sequence-of-operations-for-creating-ole-applications.md)<br/>
[数据库应用程序的创建操作顺序](../mfc/sequence-of-operations-for-creating-database-applications.md)

