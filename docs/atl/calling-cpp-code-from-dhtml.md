---
title: "Calling C++ Code from DHTML | Microsoft Docs"
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
  - "DHTML, calling C++ code from"
ms.assetid: 37329acd-4c22-40ca-a85a-b7480748f75f
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Calling C++ Code from DHTML
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

DHTML控件在容器中承载，例如测试容器或Internet Explorer。  有关如何访问测试容器的信息，请参见 [测试属性和事件与测试容器](../mfc/testing-properties-and-events-with-test-container.md)。  
  
 使用常规的控件接口，承载控件的容器与控件进行通信。  DHTML用于“”结尾通信的用户界面的与您的C\+\+代码与您的HTML资源的调度接口。  在 [修改ATL DHTML控件](../atl/modifying-the-atl-dhtml-control.md)，可以实践添加这些不同的接口调用的方法。  
  
 若要查看调用C\+\+的示例从DHTML，使用ATL控件向导的 [创建一个DHTML控件](../atl/creating-an-atl-dhtml-control.md) 代码和检查代码在标头文件并在HTML文件。  
  
## 声明在标头文件的浏览器方法  
 若要调用从DHTML用户界面的C\+\+方法，必须将方法添加到控件的用户界面接口。  例如，ATL控件向导"创建的标头文件包含C\+\+方法 `OnClick`，是向导生成的控件的用户界面接口的成员。  
  
 检查控件的.h文件的 `OnClick` :  
  
 [!code-cpp[NVC_ATL_COM#4](../atl/codesnippet/CPP/calling-cpp-code-from-dhtml_1.h)]  
  
 第一个参数，`pdispBody`，是指向主体对象的调度接口。  第二个参数，`varColor`，标识颜色应用于控件。  
  
## 调用HTML文件的C\+\+代码  
 一旦声明在标头文件的浏览器方法，可以调用方法从HTML文件。  在HTML文件的通知ATL控件向导插入三个Windows计划方法:调度消息更改控件的背景颜色的三个 `OnClick` 方法。  
  
 检查某个在HTML文件的方法:  
  
 `<BUTTON onclick='window.external.OnClick(theBody, "red");'>Red</BUTTON>`  
  
 为按钮标记的一部分，在上面的HTML代码，窗口外部方法，`OnClick`，调用。  方法有两个参数: `theBody`，引用HTML的主体文档和 `"red"`，指示控件的背景色将更改为红色，单击按钮时。  按照标记的 `Red` 是按钮的标签。  
  
 请参见 [修改ATL DHTML控件](../atl/modifying-the-atl-dhtml-control.md) 有关提供自己的方法的更多信息。  请参见 [标识DHTML控件项目的元素](../atl/identifying-the-elements-of-the-dhtml-control-project.md) 有关HTML文件的更多信息。  
  
## 请参阅  
 [支持 DHTML 控件](../atl/atl-support-for-dhtml-controls.md)