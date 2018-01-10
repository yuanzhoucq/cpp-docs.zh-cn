---
title: "将控件置于网页上 (ATL 教程，第 7) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
ms.assetid: 50dc4c95-c95b-4006-b88a-9826f7bdb222
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 523086c70d9f974c014f5d33a71bf9309b8e017d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="putting-the-control-on-a-web-page-atl-tutorial-part-7"></a>将控件置于网页上（ATL 教程，第 7 部分）
控件现已完成。 若要查看你在实际情况下运行的控件，请将其放在网页上。 定义你的控件时，已创建一个包含控件的 HTML 文件。 打开 PolyCtl.htm 文件从**解决方案资源管理器**，，您可以查看您在网页上的控件。  
  
 在此步骤中，您将编写脚本 Web 页后，可以对事件做出响应。 你还将修改要使 Internet 资源管理器知道该控件是可安全执行脚本的控件。  
  
## <a name="scripting-the-web-page"></a>脚本编写 Web 页  
 控件不执行任何操作尚未，因此更改 Web 页后，可以响应你发送的事件。  
  
#### <a name="to-script-the-web-page"></a>若要编写脚本网页  
  
1.  打开 PolyCtl.htm 并选择 HTML 视图。 将以下行添加到 HTML 代码。 它们应之后添加`</OBJECT>`之前`</BODY>`。  
  
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
  
 已添加一些从控件获取边属性并将边数增加 1，如果在控件内单击的 VBScript 代码。 如果单击控件范围之外时，你可以逐个减少边的数。  
  
## <a name="indicating-that-the-control-is-safe-for-scripting"></a>该值指示控件可安全执行脚本  
 可以在 Internet Explorer 中查看与该控件的网页或更多方便起见，使用内置于 Visual c + + 的 Web 浏览器视图。 若要查看你的控件在 Web 浏览器视图中，右键单击 PolyCtl.htm，然后单击**用浏览器查看**。  
  
 根据你当前的 Internet Explorer 安全设置，可能会收到一条安全警告对话框，其内容控件可能不是安全的脚本，并且可能损坏。 例如，如果你有一个控件，显示文件，但也出现了`Delete`删除了某个文件的方法，则可以放心如果只需在页面上查看它即可。 它将不能安全地脚本，但是，因为有人可以调用`Delete`方法。  
  
> [!IMPORTANT]
>  对于本教程中，你可以更改你在 Internet Explorer 中运行未标记为安全的 ActiveX 控件的安全设置。 在 Control Panel 中，单击**互联**单击**安全**更改相应的设置。 完成本教程后，请返回到其原始状态更改安全设置。  
  
 你可以以编程方式发出警报 Internet 资源管理器，它不需要以显示此特定的控件的安全警报对话框。 你可以执行此操作与`IObjectSafety`接口和 ATL 提供类中的此接口的实现[IObjectSafetyImpl](../atl/reference/iobjectsafetyimpl-class.md)。 若要将接口添加到你的控件，添加`IObjectSafetyImpl`到列表中继承类并添加一个条目为其 COM 映射中。  
  
#### <a name="to-add-iobjectsafetyimpl-to-the-control"></a>若要向控件添加 IObjectSafetyImpl  
  
1.  将以下行添加到 PolyCtl.h 中继承类的列表的末尾，并将逗号添加到以前的行：  
  
 [!code-cpp[NVC_ATL_Windowing#62](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_1.h)]  
  
2.  将以下行添加到 PolyCtl.h 中的 COM 映射：  
  
 [!code-cpp[NVC_ATL_Windowing#63](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_2.h)]  
  
## <a name="building-and-testing-the-control"></a>生成和测试控件  
 生成控件。 完成生成后，PolyCtl.htm 浏览器视图中再次打开。 此时，应直接没有安全警报对话框中显示网页。 在多边形; 内部单击边数加一。 要减少的边数的多边形外单击。 如果你尝试减少下面三个边数，你将看到你设置的错误消息。  
  
 [返回到步骤 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)  
  
## <a name="next-steps"></a>后续步骤  
 ATL 教程到此结束。 有关 ATL 的详细信息的链接，请参阅[ATL 起始页](../atl/active-template-library-atl-concepts.md)。  
  
## <a name="see-also"></a>请参阅  
 [教程](../atl/active-template-library-atl-tutorial.md)

