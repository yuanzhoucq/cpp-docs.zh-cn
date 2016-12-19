---
title: "Modifying the ATL DHTML Control | Microsoft Docs"
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
  - "DHTML controls"
  - "DHTML controls, 修改"
  - "HTML 控件, 修改"
ms.assetid: c053f35f-8629-4600-9595-721f5956777a
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Modifying the ATL DHTML Control
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL控件向导提供起始代码，因此您可以生成并运行控件，并且，以便您可以看到方法在项目文件中编写使用计划方案，并且，如果DHTML如何对控件的C\+\+代码。  您可以将任何计划方法添加到接口。  然后，可以调用HTML资源的方法。  
  
#### 修改ATL DHTML控件  
  
1.  在选件类视图"中，展开控件项目。  
  
     监视“于”结尾有一个方法，`OnClick`的接口。  在“于”不关闭的接口没有任何方法。  
  
2.  添加调用 `MethodInvoked`的方法添加到在“用户界面不关闭的接口”。  
  
     此方法将添加到用于控件的容器使用容器之间的交互的接口，而不是DHTML用于的接口与控件交互。  仅容器可以调用此方法。  
  
3.  如计算在.cpp文件中无存根\(stubbed\-out\)的方法并添加代码以显示消息框，例如:  
  
     [!code-cpp[NVC_ATL_COM#5](../atl/codesnippet/CPP/modifying-the-atl-dhtml-control_1.cpp)]  
  
4.  添加调用 `HelloHTML`的另一个方法，因此，只有一个，将其添加到该接口在“用户界面的末尾”。如计算在.cpp文件中无存根\(stubbed\-out\)的 `HelloHTML` 方法并添加代码以显示消息框，例如:  
  
     [!code-cpp[NVC_ATL_COM#6](../atl/codesnippet/CPP/modifying-the-atl-dhtml-control_2.cpp)]  
  
5.  添加第三种方法，`GoToURL`，到“于不关闭的接口”。通过调用 [IWebBrowser2::Navigate](https://msdn.microsoft.com/en-us/library/aa752133.aspx)执行此方法，如下所示:  
  
     [!code-cpp[NVC_ATL_COM#7](../atl/codesnippet/CPP/modifying-the-atl-dhtml-control_3.cpp)]  
  
     因为ATL提供一个指向该接口为您的.h文件中，可以使用 **IWebBrowser2** 方法。  
  
 接下来，修改HTML资源调用所创建的方法。  您将添加调用这些方法三个按钮。  
  
#### 修改HTML资源  
  
1.  在解决方案资源管理器中，双击.htm文件显示HTML资源。  
  
     检查HTML，特别是对外部Windows计划方法。  HTML调用项目的 `OnClick` 方案，并且，如果参数指示控件\(`theBody`\)和颜色的主体分配\("`red`"）。  文本在方法之后调用是出现在按钮的标签。  
  
2.  添加另一个 `OnClick` 方法，因此，只有更改颜色。  例如：  
  
    ```  
    <br>  
    <br>  
    <BUTTON onclick='window.external.OnClick(theBody, "white");'>Refresh</BUTTON>  
    ```  
  
     此方法将创建一个按钮，标记 **Refresh**，用户可以单击以返回该控件绑定到基元，白色背景。  
  
3.  添加对您创建的 `HelloHTML` 方法。  例如：  
  
    ```  
    <br>  
    <br>  
    <BUTTON onclick='window.external.HelloHTML();'>HelloHTML</BUTTON>  
    ```  
  
     此方法将创建一个按钮，标记 **HelloHTML**，用户可以单击以显示 `HelloHTML` 消息框。  
  
 现在可以编译并 [测试修改的DHTML控件](../atl/testing-the-modified-atl-dhtml-control.md)。  
  
## 请参阅  
 [支持 DHTML 控件](../atl/atl-support-for-dhtml-controls.md)