---
title: 自动化客户端：使用类型库
ms.date: 11/04/2016
f1_keywords:
- MkTypLib
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
ms.openlocfilehash: e5f9ffcebc3725851c599e7b21369f45d0029d81
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626091"
---
# <a name="automation-clients-using-type-libraries"></a>自动化客户端：使用类型库

如果客户端要操作服务器的对象，则自动化客户端必须具有有关服务器对象的属性和方法的信息。 属性具有数据类型;方法经常返回值和接受参数。 为了静态绑定到服务器对象类型，客户端需要所有这些数据类型的相关信息。

可以通过多种方式知道此类型信息。 推荐的方法是创建类型库。

有关[mktyplib.exe](/windows/win32/Midl/differences-between-midl-and-mktyplib)的信息，请参阅 Windows SDK。

Visual C++ 可以读取类型库文件，并创建派生自[COleDispatchDriver](reference/coledispatchdriver-class.md)的调度类。 该类的对象具有属性和操作，以复制服务器对象的属性和操作。 您的应用程序将调用此对象的属性和操作，而从路由这些调用的函数继承的功能将 `COleDispatchDriver` 它们路由到服务器对象。

如果选择在创建项目时包含自动化，Visual C++ 会自动为你维护此类型库文件。 作为每个生成的一部分，将用 Mktyplib.exe 生成 .tlb 文件。

### <a name="to-create-a-dispatch-class-from-a-type-library-tlb-file"></a>从类型库（.tlb）文件创建调度类

1. 在类视图或解决方案资源管理器中，右键单击项目，然后单击 "**添加**"，然后单击快捷菜单上的 "**添加类**"。

1. 在 "**添加类**" 对话框中，选择左窗格中的 " **Visual C++/MFC** " 文件夹。 从右侧窗格中选择 "**类型库中的 MFC 类**" 图标，然后单击 "**打开**"。

1. 在 "**从 Typelib 添加类向导**" 对话框中，从 "**可用的类型库**" 下拉列表中选择类型库。 "**接口**" 框显示用于选定类型库的接口。

    > [!NOTE]
    >  可以从多个类型库中选择接口。

   若要选择接口，请双击它们或单击 "**添加**" 按钮。 当你这样做时，调度类的名称将显示在 "**生成的类**" 框中。 您可以在框中编辑类名称 `Class` 。

   "**文件**" 框显示将在其中声明类的文件。 （也可以编辑此文件名）。 如果希望将标头和实现信息写入到现有文件中或项目目录以外的目录中，也可以使用 "浏览" 按钮选择其他文件。

    > [!NOTE]
    >  所选接口的所有调度类都将放入此处指定的文件。 如果要在单独的标头中声明接口，则必须为要创建的每个头文件运行此向导。

    > [!NOTE]
    >  某些类型库信息可以存储在文件中。DLL：。OCX 或。.OLB 文件扩展名。

1. 单击“完成”。

   然后，该向导将使用指定的类和文件名为调度类编写代码。

## <a name="see-also"></a>另请参阅

[自动化客户端](automation-clients.md)
