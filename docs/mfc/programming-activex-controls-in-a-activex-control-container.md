---
title: ActiveX 控件容器： 对 ActiveX 控件容器中的 ActiveX 控件编程 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActiveX control containers [MFC], accessing ActiveX controls
- Confirm Classes dialog box
- wrapper classes [MFC], ActiveX controls
- ActiveX control containers [MFC], wrapper classes
- ActiveX controls [MFC], accessing
- MFC ActiveX controls [MFC], accessing in containers
- header files [MFC], for ActiveX control wrapper class
- wrapper classes [MFC], using
- ActiveX controls [MFC], wrapper classes
ms.assetid: ef9b2480-92d6-4191-b16e-8055c4fd7b73
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2204df82263cdd39d7f78ff43cc2c02a7eafbac5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379796"
---
# <a name="activex-control-containers-programming-activex-controls-in-an-activex-control-container"></a>ActiveX 控件容器：对 ActiveX 控件容器中的 ActiveX 控件编程

本文介绍了用于访问已公开过程[方法](../mfc/mfc-activex-controls-methods.md)并[属性](../mfc/mfc-activex-controls-properties.md)嵌入 ActiveX 控件。

>[!IMPORTANT]
> ActiveX 是一项传统技术，不应使用新的开发。 本文将取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。

基本上，将执行以下步骤：

1. [将 ActiveX 控件插入到 ActiveX 容器项目](../mfc/inserting-a-control-into-a-control-container-application.md)使用库中。

1. [定义的成员变量](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)（或其他形式的访问权限） 的类型相同，ActiveX 控件包装器类。

1. [ActiveX 控件编程](#_core_programming_the_activex_control)使用预定义的包装器类的成员函数。

本次讨论中，假定已创建了基于对话框的项目 （名为容器） 中使用 ActiveX 控件支持。 Circ 控件示例，Circ，将添加到生成的项目。

一旦 Circ 控件插入到项目 （步骤 1） 时，插入应用程序的主对话框 Circ 控件的实例。

## <a name="procedures"></a>过程

#### <a name="to-add-the-circ-control-to-the-dialog-template"></a>Circ 控件添加到对话框模板

1. 加载 ActiveX 控件容器项目。 对于此示例中，使用`Container`项目。

1. 单击资源视图选项卡。

1. 打开**对话框**文件夹。

1. 双击主对话框模板。 对于此示例中，使用**IDD_CONTAINER_DIALOG**。

1. 单击工具箱上的 Circ 控件图标。

1. 对话框可以将插入 Circ 控件内单击。

1. 从**文件**菜单中，选择**全部保存**保存到对话框模板的所有修改。

## <a name="modifications-to-the-project"></a>项目的修改

若要启用容器应用程序访问 Circ 控件，Visual c + + 会自动添加包装类 (`CCirc`) 实现文件 (。CPP) 到容器项目，并包装类头文件 (。H） 对话框标头文件的文件：

[!code-cpp[NVC_MFC_AxCont#1](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_1.h)]

##  <a name="_core_the_wrapper_class_header_28h29_file"></a> 包装类头文件 (。H） 文件

若要获取和设置属性 （和调用的方法） 为 Circ 控件`CCirc`包装器类提供了所有公开的方法和属性的声明。 在示例中，这些声明位于 CIRC.H. 下面的示例是类的部分`CCirc`，它定义的 ActiveX 控件公开的接口：

[!code-cpp[NVC_MFC_AxCont#2](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_2.h)]
[!code-cpp[NVC_MFC_AxCont#3](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_3.h)]

然后可以从其他应用程序的过程使用普通的 c + + 语法调用这些函数。 使用此成员函数设置为访问控件的方法和属性的详细信息，请参阅明[ActiveX 控件编程](#_core_programming_the_activex_control)。

##  <a name="_core_member_variable_modifications_to_the_project"></a> 项目的成员变量修改

后已添加到项目中并在对话框容器中嵌入 ActiveX 控件，它可以访问的项目的其他部分。 访问控制的最简单方法是向[创建一个成员变量](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)的对话框类中， `CContainerDlg` （步骤 2），即添加到项目中 Visual c + + 包装器类的类型相同。 成员变量然后可用于在任何时间访问嵌入的控件。

当**添加成员变量**对话框中添加*m_circctl*成员变量到项目时，它还将添加以下代码行到标头文件 (。H） 的`CContainerDlg`类：

[!code-cpp[NVC_MFC_AxCont#4](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_4.h)]
[!code-cpp[NVC_MFC_AxCont#5](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_5.h)]

此外，调用**DDX_Control**自动添加到`CContainerDlg`的实现`DoDataExchange`:

[!code-cpp[NVC_MFC_AxCont#6](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_6.cpp)]

##  <a name="_core_programming_the_activex_control"></a> ActiveX 控件编程

此时，已插入 ActiveX 控件到对话框模板，并为其创建的成员变量。 常见的 c + + 语法现在可用于访问的属性和嵌入控件的方法。

如所述 (在[包装类头文件 (。H） 文件](#_core_the_wrapper_class_header_28h29_file))，该标头文件 (。H） 为`CCirc`包装器类，在此事例 CIRC.H，包含可用于获取和设置的任何公开的属性值的成员函数的列表。 此外，还提供公开的方法的成员函数。

若要修改控件的属性的常见位置是在`OnInitDialog`主对话框类的成员函数。 对话框中显示，用于初始化其内容，包括其任何控件之前调用此函数。

下面的代码示例使用*m_circctl*成员变量来修改嵌入的 Circ 控件的标题和 CircleShape 属性：

[!code-cpp[NVC_MFC_AxCont#7](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_7.cpp)]

## <a name="see-also"></a>请参阅

[ActiveX 控件容器](../mfc/activex-control-containers.md)

