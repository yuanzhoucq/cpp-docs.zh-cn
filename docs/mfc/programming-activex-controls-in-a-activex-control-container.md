---
title: ActiveX 控件容器：对 ActiveX 控件容器中的 ActiveX 控件编程
ms.date: 09/12/2018
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
ms.openlocfilehash: 9620f4d47197147db4972c9f2024f6018a705902
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371190"
---
# <a name="activex-control-containers-programming-activex-controls-in-an-activex-control-container"></a>ActiveX 控件容器：对 ActiveX 控件容器中的 ActiveX 控件编程

本文介绍了访问嵌入式 ActiveX 控件的公开[方法和](../mfc/mfc-activex-controls-methods.md)[属性](../mfc/mfc-activex-controls-properties.md)的过程。

>[!IMPORTANT]
> ActiveX 是一种不应用于新开发的传统技术。 有关取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。

基本上，您将按照以下步骤操作：

1. 使用库[将 ActiveX 控件插入到 ActiveX 容器项目中](../mfc/inserting-a-control-into-a-control-container-application.md)。

1. [定义与](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)ActiveX 控件包装类类型相同的成员变量（或其他形式的访问）。

1. 使用包装类的预定义成员函数[对 ActiveX 控件进行编程](#_core_programming_the_activex_control)。

对于此讨论，假设您创建了一个基于对话框的项目（名为容器），支持 ActiveX 控件。 Circ 样本控制，Circ，将添加到生成的项目中。

将 Circ 控件插入到项目（步骤 1）后，将 Circ 控件的实例插入到应用程序的主对话框中。

## <a name="procedures"></a>过程

#### <a name="to-add-the-circ-control-to-the-dialog-template"></a>将 Circ 控件添加到对话框模板

1. 加载 ActiveX 控制容器项目。 在此示例中，请使用项目`Container`。

1. 单击"资源视图"选项卡。

1. 打开**对话框**文件夹。

1. 双击主对话框模板。 在此示例中，请使用**IDD_CONTAINER_DIALOG**。

1. 单击工具箱上的 Circ 控件图标。

1. 单击对话框中的一个点以插入 Circ 控件。

1. 在 **"文件"** 菜单中，选择 **"全部保存"** 以保存对对话框模板的所有修改。

## <a name="modifications-to-the-project"></a>对项目的修改

为了使容器应用程序能够访问 Circ 控件，Visual C++ 自动添加包装类 （`CCirc`） 实现文件 （。CPP）到容器项目和包装类标头 （。H） 文件到对话框头文件：

[!code-cpp[NVC_MFC_AxCont#1](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_1.h)]

## <a name="the-wrapper-class-header-h-file"></a><a name="_core_the_wrapper_class_header_28h29_file"></a>包装类标头 （.H） 文件

要获取和设置 Circ 控件的属性（和调用方法），`CCirc`包装类提供所有公开方法和属性的声明。 在此示例中，这些声明见于中国保监会。H。 以下示例是定义 ActiveX`CCirc`控件公开接口的类部分：

[!code-cpp[NVC_MFC_AxCont#2](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_2.h)]
[!code-cpp[NVC_MFC_AxCont#3](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_3.h)]

然后，可以使用正常的C++语法从应用程序的其他过程调用这些函数。 有关使用此成员函数集访问控件的方法和属性的详细信息，请参阅[编程 ActiveX 控件](#_core_programming_the_activex_control)的部分。

## <a name="member-variable-modifications-to-the-project"></a><a name="_core_member_variable_modifications_to_the_project"></a>对项目的成员变量修改

将 ActiveX 控件添加到项目中并嵌入到对话框容器中后，项目的其他部分可以访问它。 访问控件的最简单方法是创建对话框类`CContainerDlg`[的成员变量](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)（步骤 2），该变量的类型与 Visual C++添加到项目的包装类类型相同。 然后，您可以随时使用成员变量访问嵌入控件。

当 **"添加成员变量"** 对话框将*m_circctl*成员变量添加到项目中时，它还向标头文件 （） 添加以下行。H）`CContainerDlg`类：

[!code-cpp[NVC_MFC_AxCont#4](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_4.h)]
[!code-cpp[NVC_MFC_AxCont#5](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_5.h)]

此外，对**DDX_Control**的调用会自动添加到`CContainerDlg`的 实现中： `DoDataExchange`

[!code-cpp[NVC_MFC_AxCont#6](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_6.cpp)]

## <a name="programming-the-activex-control"></a><a name="_core_programming_the_activex_control"></a>编程 ActiveX 控件

此时，您已将 ActiveX 控件插入到对话框模板中，并为其创建了一个成员变量。 现在可以使用常用C++语法来访问嵌入控件的属性和方法。

如前所述（在[包装类标题（中）。H） 文件](#_core_the_wrapper_class_header_28h29_file)），头文件 （。H） 包装`CCirc`类，在这种情况下，中国保监会。H，包含可用于获取和设置任何公开属性值的成员函数的列表。 公开方法的成员函数也可用。

修改控件属性的常见位置位于主对话框类`OnInitDialog`的成员函数中。 此函数在对话框出现之前调用，用于初始化其内容，包括其任何控件。

以下代码示例使用*m_circctl*成员变量修改嵌入式 Circ 控件的标题和 CircleShape 属性：

[!code-cpp[NVC_MFC_AxCont#7](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_7.cpp)]

## <a name="see-also"></a>另请参阅

[ActiveX 控制容器](../mfc/activex-control-containers.md)
