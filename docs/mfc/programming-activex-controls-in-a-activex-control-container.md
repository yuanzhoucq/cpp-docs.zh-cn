---
title: ActiveX 控件容器： 对 ActiveX 控件容器中的 ActiveX 控件编程 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: bae926cfc7e83edeef9ee68c7ce7118c55009a08
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="activex-control-containers-programming-activex-controls-in-an-activex-control-container"></a>ActiveX 控件容器：对 ActiveX 控件容器中的 ActiveX 控件编程
本文介绍了用于访问公开过程[方法](../mfc/mfc-activex-controls-methods.md)和[属性](../mfc/mfc-activex-controls-properties.md)的嵌入 ActiveX 控件。 基本上，你将执行下列步骤：  
  
1.  [ActiveX 控件插入 ActiveX 容器项目](../mfc/inserting-a-control-into-a-control-container-application.md)使用库。  
  
2.  [定义的成员变量](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)（或其他形式的访问权限） 与 ActiveX 相同类型的控件包装类。  
  
3.  [ActiveX 控件编程](#_core_programming_the_activex_control)使用预定义的包装类成员函数。  
  
 本主题中，假定与 ActiveX 控件支持的你已创建 （名为容器） 的、 基于对话框的项目。 Circ 控件示例，Circ，将添加到生成的项目。  
  
 Circ 控件插入项目 （步骤 1） 后, 插入应用程序的主对话框 Circ 控件的实例。  
  
## <a name="procedures"></a>过程  
  
#### <a name="to-add-the-circ-control-to-the-dialog-template"></a>Circ 控件添加到对话框模板  
  
1.  加载 ActiveX 控件容器项目。 对于此示例中，使用`Container`项目。  
  
2.  单击资源视图选项卡。  
  
3.  打开**对话框**文件夹。  
  
4.  双击主对话框模板。 对于此示例中，使用**IDD_CONTAINER_DIALOG**。  
  
5.  单击工具箱上的 Circ 控件图标。  
  
6.  单击对话框中要插入 Circ 控件内的位置。  
  
7.  从**文件**菜单上，选择**保存所有**保存到对话框模板的所有修改。  
  
## <a name="modifications-to-the-project"></a>项目的修改  
 若要启用容器应用程序访问 Circ 控件，Visual c + +，会自动添加包装类 (`CCirc`) 实现文件 (。CPP) 到容器项目和包装类头文件 (。H） 文件与对话框框标头文件：  
  
 [!code-cpp[NVC_MFC_AxCont#1](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_1.h)]  
  
##  <a name="_core_the_wrapper_class_header_28h29_file"></a> 包装类头文件 (。H） 文件  
 获取并设置属性 （和调用方法） Circ 控件`CCirc`包装类进行的所有公开的方法和属性的声明。 在示例中，这些声明位于 CIRC.H。 下面的示例是类的部分`CCirc`，它定义的 ActiveX 控件公开的接口：  
  
 [!code-cpp[NVC_MFC_AxCont#2](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_2.h)]  
[!code-cpp[NVC_MFC_AxCont#3](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_3.h)]  
  
 然后，可以调用这些函数与其他应用程序的过程使用常规 c + + 语法。 使用此设置以访问控件的方法和属性的成员函数的详细信息，请参阅明[编程 ActiveX 控件](#_core_programming_the_activex_control)。  
  
##  <a name="_core_member_variable_modifications_to_the_project"></a> 项目的成员变量修改  
 添加到项目并在对话框容器中嵌入 ActiveX 控件后，项目的其他部分可以访问该。 访问控制的最简单方法是到[创建成员变量](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)的对话框类中， `CContainerDlg` （步骤 2），即包装类添加到项目中 Visual c + + 通过与同一类型。 然后可以使用成员变量在任何时访问嵌入的控件。  
  
 当**添加成员变量**对话框中添加`m_circctl`成员变量项目，它还将添加以下行到标头文件 (。H） 的`CContainerDlg`类：  
  
 [!code-cpp[NVC_MFC_AxCont#4](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_4.h)]  
[!code-cpp[NVC_MFC_AxCont#5](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_5.h)]  
  
 此外，调用**DDX_Control**自动添加到`CContainerDlg`的实现`DoDataExchange`:  
  
 [!code-cpp[NVC_MFC_AxCont#6](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_6.cpp)]  
  
##  <a name="_core_programming_the_activex_control"></a> ActiveX 控件编程  
 此时，你已插入 ActiveX 控件到对话框模板，并且为其创建的成员变量。 你现在可以使用常见的 c + + 语法访问的属性和方法的嵌入的控件。  
  
 所述 (在[包装类头文件 (。H） 文件](#_core_the_wrapper_class_header_28h29_file))，该标头文件 (。H） 为`CCirc`包装器类，在此案例 CIRC.H，包含可用于获取和设置的任何公开的属性值的成员函数的列表。 此外，还提供公开的方法的成员函数。  
  
 若要修改控件的属性的常见位置是在`OnInitDialog`主对话框类的成员函数。 该对话框中显示，用来初始化其内容，包括其任何控件之前调用此函数。  
  
 下面的代码示例使用`m_circctl`成员变量来修改嵌入的 Circ 控件的标题和 CircleShape 属性：  
  
 [!code-cpp[NVC_MFC_AxCont#7](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_7.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [ActiveX 控件容器](../mfc/activex-control-containers.md)

