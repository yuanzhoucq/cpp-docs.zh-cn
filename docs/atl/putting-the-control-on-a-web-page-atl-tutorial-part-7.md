---
title: "将控件置于网页上（ATL 教程，第 7 部分） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
ms.assetid: 50dc4c95-c95b-4006-b88a-9826f7bdb222
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 将控件置于网页上（ATL 教程，第 7 部分）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您的控件现已完成。  若要查看实际情况中的控件工作，请将其置于网页上。  在您定义控件时会创建包含控件的 HTML 文件。  打开“解决方案资源管理器”的 PolyCtl.htm 文件，这样您可以看到网页上的控件。  
  
 在此步骤中，您将给网页编写脚本以响应事件。  您也将修改控件以使 Internet Explorer 知道用于脚本的控件是安全的。  
  
## 编写 web 页面脚本  
 控件仍未执行任何操作，因此，请更改网页以响应您发送的事件。  
  
#### 编写网页脚本  
  
1.  打开 PolyCtl.htm 并选择 HTML 视图。  将以下各行添加到 HTML 代码中。  应将它们添加在 `</OBJECT>` 之后，但位于 `</BODY>` 之前。  
  
    ```  
  
    <SCRIPT LANGUAGE="VBScript">  
    <!--  
    Sub PolyCtl_ClickIn(x, y)  
       PolyCtl.Sides = PolyCtl.Sides + 1  
    End Sub  
    Sub PolyCtl_ClickOut(x, y)  
       PolyCtl.Sides = PolyCtl.Sides - 1  
    End Sub  
    -->  
    </SCRIPT>  
    ```  
  
2.  保存 HTM 文件。  
  
 您已添加一些 VBScript 代码，其从控件获取 Sides 属性，并且如果在控件内单击可将边的数量加一。  如果在控件外单击，则将减少一个边数。  
  
## 指示脚本的控件是安全的  
 您可使用 Internet Explorer 中的控件查看网页，或更方便地，使用 Web 浏览器查看 Visual C\+\+ 中的生成。  若要在 Web 浏览器视图中查看控件，请右键单击 PolyCtl.htm，然后单击“在浏览器中查看”。  
  
 根据您当前的 Internet Explorer 安全设置，您可能会收到安全警报对话框，告诉您控件可能对于脚本是不安全的并可能造成损害。  例如，如果有一个控件，能够显示文件并具有删除文件的 `Delete` 方法，则只在页面上查看该控件是安全的。  因为有人可能调用 `Delete` 方法，所以编写脚本可能不安全。  
  
> [!IMPORTANT]
>  关于本教程，您可以更改您在 Internet Explorer 中的安全设置，以运行未标记为安全的 ActiveX 控件。  在控制面板中单击“Internet 属性”，并单击“安全”以更改恰当的设置。  在完成本教程后，将您的安全设置更改回其原始状态。  
  
 您可通过编程方式警告 Internet Explorer：无需显示针对此特定控件的“安全警报”对话框。  您可使用 `IObjectSafety` 接口执行此操作，并且 ATL 在类 [IObjectSafetyImpl](../atl/reference/iobjectsafetyimpl-class.md) 中提供此接口的实现。  若要将接口添加到控件，请将 `IObjectSafetyImpl` 添加到继承类列表并在 COM 映射中为其添加条目。  
  
#### 将 IObjectSafetyImpl 添加到控件  
  
1.  将下行添加到 PolyCtl.h 中继承类的列表末尾，并在上一行添加一个逗号：  
  
     [!code-cpp[NVC_ATL_Windowing#62](../atl/codesnippet/CPP/putting-the-control-on-a-web-page-atl-tutorial-part-7_1.h)]  
  
2.  将下行添加到 PolyCtl.h 中的 COM 映射中：  
  
     [!code-cpp[NVC_ATL_Windowing#63](../atl/codesnippet/CPP/putting-the-control-on-a-web-page-atl-tutorial-part-7_2.h)]  
  
## 生成和测试控件  
 生成控件。  生成完成后，在浏览器视图中再次打开 PolyCtl.htm。  此时，将直接显示网页而无需显示“安全警报”对话框。  单击多边形的内部；边数增加 1。  单击多边形的外部以减少边数。  如果您尝试将边数减少到三条以下，将显示您设置的错误消息。  
  
 [返回步骤 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)  
  
## 后续步骤  
 本步骤将结束 ATL 教程。  有关指向 ATL 更多信息的链接，请参阅 [ATL 起始页](../atl/active-template-library-atl-concepts.md)。  
  
## 请参阅  
 [教程](../atl/active-template-library-atl-tutorial.md)