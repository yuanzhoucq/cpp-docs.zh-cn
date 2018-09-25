---
title: 自动化客户端： 使用类型库 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- MkTypLib
dev_langs:
- C++
helpviewer_keywords:
- clients, Automation
- dispatch class [MFC]
- Automation clients, type libraries
- type libraries, Automation clients
- ODL (Object Description Language)
- ODL files
- classes [MFC], dispatch
- MkTypLib tool
- .odl files
ms.assetid: d405bc47-118d-4786-b371-920d035b2047
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 421040024e5dd95fb39bdc78cd54f3f7dc49bf83
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377703"
---
# <a name="automation-clients-using-type-libraries"></a>自动化客户端：使用类型库

自动化客户端必须具有服务器对象的属性和方法有关的信息，如果客户端操作的服务器的对象。 属性具有的数据类型;方法通常返回的值，并接受参数。 客户端需要有关数据类型的所有这些信息才能以静态方式绑定到的服务器对象类型。

此类型信息可通过多种方式。 建议的方法是创建类型库。

有关的信息[MkTypLib](/windows/desktop/Midl/differences-between-midl-and-mktyplib)，请参阅 Windows SDK。

Visual c + + 可以读取类型库文件和创建调度类派生自[COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)。 该类的对象具有属性和复制这些服务器对象的操作。 你的应用程序调用此对象的属性和操作，并继承其功能`COleDispatchDriver`这些将呼叫路由到 OLE 系统，又将其路由到的服务器对象。

Visual c + + 自动维护此类型库文件，如果您选择要创建项目时包括自动化。 为每个生成的一部分，将使用 MkTypLib 构建.tlb 文件。

### <a name="to-create-a-dispatch-class-from-a-type-library-tlb-file"></a>若要从类型库 (.tlb) 文件创建调度类

1. 在类视图或解决方案资源管理器中，右键单击项目，然后单击**外**，然后单击**添加类**快捷菜单上。

1. 在中**添加类**对话框中，选择**Visual c + + MFC**的左窗格中的文件夹。 选择**从类型库的 MFC 类**从右窗格中单击图标**打开**。

1. 在中**从类型库向导添加类**对话框框中，选择从类型库**可用的类型库**下拉列表。 **接口**框将显示可用于所选的类型库的接口。

    > [!NOTE]
    >  您可以选择从多个类型库的接口。

     若要选择的接口，双击它们或单击**添加**按钮。 执行此操作时，调度类的名称将出现在**生成的类**框。 您可以编辑中的类名称`Class`框。

     **文件**框显示将在其中声明类的文件。 （可以编辑此文件名）。 此外可以使用浏览按钮以选择其他文件，如果想要编写在现有文件或项目目录之外的目录中的标头和实现信息。

    > [!NOTE]
    >  所选接口的所有调度类都将都放到此处指定的文件。 如果你想要在单独的标头中声明的接口，则必须运行此向导为你想要创建每个标头文件。

    > [!NOTE]
    >  类型库的一些信息可能存储在使用的文件。DLL。OCX，或。OLB 文件扩展名。

1. 单击 **“完成”**。

     该向导将然后编写您使用指定的类和文件名称的调度类的代码。

## <a name="see-also"></a>请参阅

[自动化客户端](../mfc/automation-clients.md)

