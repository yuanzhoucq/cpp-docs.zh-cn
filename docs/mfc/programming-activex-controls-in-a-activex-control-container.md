---
title: "ActiveX 控件容器：对 ActiveX 控件容器中的 ActiveX 控件编程 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控件容器 [C++], 访问 ActiveX 控件"
  - "ActiveX 控件容器 [C++], 包装类"
  - "ActiveX 控件 [C++], 访问"
  - "ActiveX 控件 [C++], 包装类"
  - "“确认类”对话框"
  - "头文件 [C++], 对于 ActiveX 控件包装类"
  - "MFC ActiveX 控件 [C++], 在容器中访问"
  - "包装类 [C++], ActiveX 控件"
  - "包装类 [C++], using"
ms.assetid: ef9b2480-92d6-4191-b16e-8055c4fd7b73
caps.latest.revision: 8
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ActiveX 控件容器：对 ActiveX 控件容器中的 ActiveX 控件编程
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文描述的访问公开的 ActiveX 控件嵌入的 [方法](../mfc/mfc-activex-controls-methods.md)[属性](../mfc/mfc-activex-controls-properties.md) 和过程。  基本上，您将执行以下步骤：  
  
1.  使用 库的[插入到 ActiveX 容器 ActiveX 控件项目](../mfc/inserting-a-control-into-a-control-container-application.md)。  
  
2.  [定义的成员变量](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) \(或访问其他窗体\) 相同类型作为 ActiveX 控件包装类。  
  
3.  使用包装类中的预定义的成员函数上的[编程 ActiveX 控件](#_core_programming_the_activex_control)。  
  
 对于本讨论中，假设您创建了基于对话框的项目 \(名为\) 的容器 ActiveX 控件。  Circ 示例控件，Circ，将添加到生成的项目。  
  
 一旦 Circ 控件插入到项目 \(步骤 1\)，Circ 插入控件的实例放置到应用程序的主对话框。  
  
## 过程  
  
#### 添加 Circ 控件添加到对话框模板  
  
1.  ActiveX 控件容器加载项目。  对于此例，请使用 `Container` 项目。  
  
2.  单击“资源视图”选项卡。  
  
3.  打开 **对话框** 文件夹。  
  
4.  双击主对话框模板。  对于此例，请使用 **IDD\_CONTAINER\_DIALOG**。  
  
5.  单击工具箱上的 Circ 控件图标。  
  
6.  单击对话框中的一个、Circ 插入控件。  
  
7.  从 **文件** 菜单中，选择 **全部保存** 保存到对话框模板的所有修改。  
  
## 为修改项目  
 若要启用容器应用程序访问 Circ 控件，Visual C\+\+ 会自动将包装类 \(`CCirc`\) 实现文件 \(.cpp\) 到容器项目和包装类 \(标题。H 到对话框\) 头文件的文件：  
  
 [!code-cpp[NVC_MFC_AxCont#1](../mfc/codesnippet/CPP/programming-activex-controls-in-a-activex-control-container_1.h)]  
  
##  <a name="_core_the_wrapper_class_header_28h29_file"></a> 包装类 \(标题。H\) 文件  
 若要获取和设置属性 \(并调用方法\) Circ 控件，`CCirc` 包装类提供所有公开的方法和属性的声明。  在该示例中，以下声明在 CIRC.H. 找到。  下面的示例为定义 ActiveX 控件的公开接口类的 `CCirc` 部分：  
  
 [!code-cpp[NVC_MFC_AxCont#2](../mfc/codesnippet/CPP/programming-activex-controls-in-a-activex-control-container_2.h)]  
[!code-cpp[NVC_MFC_AxCont#3](../mfc/codesnippet/CPP/programming-activex-controls-in-a-activex-control-container_3.h)]  
  
 使用常规 C\+\+ 语法，这些函数可以从其他应用程序的过程然后调用。  有关使用此成员函数集的更多信息，请参见 [编程 ActiveX 控件](#_core_programming_the_activex_control)节控制访问方法和属性。  
  
##  <a name="_core_member_variable_modifications_to_the_project"></a> 为项目成员变量的修改  
 在 ActiveX 控件在容器被添加到项目，并嵌入其可以由项目的其他部分访问。  简单的访问方法控件是对类的对话框，[创建成员变量](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)`CContainerDlg` \(步骤 2\)，是类型相同的和包装类添加到项目。Visual C\+\+。  可以使用成员变量随时访问嵌入的控件。  
  
 在 **添加成员变量** 对话框将 `m_circctl` 成员变量添加到项目时，它还添加下面一行代码添加到头文件中 \(。`CContainerDlg` 类的 H\):  
  
 [!code-cpp[NVC_MFC_AxCont#4](../mfc/codesnippet/CPP/programming-activex-controls-in-a-activex-control-container_4.h)]  
[!code-cpp[NVC_MFC_AxCont#5](../mfc/codesnippet/CPP/programming-activex-controls-in-a-activex-control-container_5.h)]  
  
 此外，对 **DDX\_Control** 的调用会自动添加到 `DoDataExchange`的 `CContainerDlg` 实现：  
  
 [!code-cpp[NVC_MFC_AxCont#6](../mfc/codesnippet/CPP/programming-activex-controls-in-a-activex-control-container_6.cpp)]  
  
##  <a name="_core_programming_the_activex_control"></a> 编程 ActiveX 控件  
 此时，您将插入 ActiveX 控件添加到对话框模板并为其创建的成员变量。  现在可以使用"一般 C\+\+ 语法访问嵌入式控件的属性和方法。  
  
 作为在头文件注释 \( [包装类 \(标题。H\) 文件](#_core_the_wrapper_class_header_28h29_file)\)，\(。`CCirc` 包装类的 H\)，在这种情况下，CIRC.H 包含列表成员函数可以使用获取并设置所有公开的属性值。  公开的方法成员函数也可用。  
  
 修改控件属性的公共可在主对话框类的 `OnInitDialog` 成员函数。  调用该函数时，在对话框中显示并使用初始化之前，其内容包括任何控件。  
  
 下面的代码示例使用 `m_circctl` 成员变量来修改 Circ 嵌入的控件的标题和 CircleShape 属性：  
  
 [!code-cpp[NVC_MFC_AxCont#7](../mfc/codesnippet/CPP/programming-activex-controls-in-a-activex-control-container_7.cpp)]  
  
## 请参阅  
 [ActiveX 控件容器](../mfc/activex-control-containers.md)