---
title: "修改 ATL DHTML 控件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- HTML controls, modifying
- DHTML controls
- DHTML controls, modifying
ms.assetid: c053f35f-8629-4600-9595-721f5956777a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 571b7f4f52e3f6838822db39ba0bbf5148d57d1e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="modifying-the-atl-dhtml-control"></a>修改 ATL DHTML 控件
ATL 控件向导提供起始代码，以便你可以生成并运行该控件，因此你可以查看在项目文件中写入这些方法的方式以及如何 DHTML 调用到控件的 c + + 代码中使用调度方法。 可以将任何调度方法添加到接口。 然后，你可以在 HTML 资源调用方法。  
  
#### <a name="to-modify-the-atl-dhtml-control"></a>若要修改 ATL DHTML 控件  
  
1.  在类视图中，展开控件项目。  
  
     请注意，在"用户界面"中结束的接口包含一个方法， `OnClick`。 不是以"用户界面"结尾的接口没有任何方法。  
  
2.  添加一个方法，该方法调用`MethodInvoked`不是以"UI。"结尾的接口  
  
     此方法将添加到用于控件容器中的容器交互，而不是 DHTML 用于与控件交互的接口的接口。 只有的容器才可以调用此方法。  
  
3.  在.cpp 文件中找到的存根处理扩展方法，然后添加代码来显示一个消息框，例如：  
  
 [!code-cpp[NVC_ATL_COM#5](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_1.cpp)]  
  
4.  添加另一种方法调用`HelloHTML`，仅此期间，将其添加到"用户界面。"中结束的接口 找出存根处理`HelloHTML`方法在.cpp 文件，并添加代码以显示一个消息框，例如：  
  
 [!code-cpp[NVC_ATL_COM#6](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_2.cpp)]  
  
5.  添加第三个方法， `GoToURL`，不是以"UI。"结尾的接口 实现此方法通过调用[IWebBrowser2::Navigate](https://msdn.microsoft.com/library/aa752133.aspx)、，如下所示：  
  
 [!code-cpp[NVC_ATL_COM#7](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_3.cpp)]  
  
     你可以使用**IWebBrowser2**方法因为 ATL.h 文件中为你提供到该接口的指针。  
  
 接下来，修改要调用你创建的方法的 HTML 资源。 你将添加三个按钮，以调用这些方法。  
  
#### <a name="to-modify-the-html-resource"></a>若要修改的 HTML 资源  
  
1.  在解决方案资源管理器中，双击要显示的 HTML 资源的.htm 文件。  
  
     检查的 HTML，尤其是对外部的 Windows 调度方法的调用。 HTML 调用项目的`OnClick`方法和参数指示该控件的正文 (`theBody`) 和分配的颜色 ("`red`")。 此方法调用后面的文本是在按钮显示的标签。  
  
2.  添加另一个`OnClick`方法，仅更改颜色。 例如:  
  
 ```  
 <br>  
 <br>  
 <BUTTON onclick='window.external.OnClick(theBody, "white");'>Refresh</BUTTON>  
 ```  
  
     此方法将创建标记的按钮**刷新**，用户可以单击以将控件返回到原始的白色背景。  
  
3.  添加对的调用`HelloHTML`你创建的方法。 例如:  
  
 ```  
 <br>  
 <br>  
 <BUTTON onclick='window.external.HelloHTML();'>HelloHTML</BUTTON>  
 ```  
  
     此方法将创建标记的按钮**HelloHTML**，用户可以单击以显示`HelloHTML`消息框。  
  
 现在可以生成和[测试修改后的 DHTML 控件](../atl/testing-the-modified-atl-dhtml-control.md)。  
  
## <a name="see-also"></a>请参阅  
 [支持 DHTML 控件](../atl/atl-support-for-dhtml-controls.md)

