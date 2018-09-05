---
title: 修改 ATL DHTML 控件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HTML controls, modifying
- DHTML controls
- DHTML controls, modifying
ms.assetid: c053f35f-8629-4600-9595-721f5956777a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a0652ca867ba49243ca5c87caa1dec98da929cf
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764545"
---
# <a name="modifying-the-atl-dhtml-control"></a>修改 ATL DHTML 控件

ATL 控件向导提供了起始代码，这样可以生成并运行该控件，因此您可以查看项目文件中写入方法的方式以及如何 DHTML 调用到控件的 c + + 代码中使用的调度方法。 可以将任何 dispatch 方法添加到该接口。 然后，您可以在 HTML 资源调用方法。

#### <a name="to-modify-the-atl-dhtml-control"></a>若要修改的 ATL DHTML 控件

1. 在类视图中，展开控件项目。

   请注意以"UI"结尾的接口，有一种方法， `OnClick`。 不是以"UI"结尾的接口没有任何方法。

2. 添加一个名为方法`MethodInvoked`到不是以"UI。"结尾的接口

   此方法将添加到在控件容器用于容器交互，而不是 DHTML 用来与控件交互的接口的接口。 仅在容器可以调用此方法。

3. 在.cpp 文件中找到无存根方法，并添加代码以显示一个消息框，例如：

   [!code-cpp[NVC_ATL_COM#5](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_1.cpp)]

4. 添加另一种方法称为`HelloHTML`，但这次，将其添加到"用户界面。"中结束的接口 找出用作存根`HelloHTML`方法在.cpp 文件，并添加代码以显示一个消息框，例如：

   [!code-cpp[NVC_ATL_COM#6](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_2.cpp)]

5. 添加第三种方法， `GoToURL`，到不是以"UI。"结尾的接口 实现此方法通过调用[IWebBrowser2::Navigate](https://msdn.microsoft.com/library/aa752133.aspx)，按如下所示：

   [!code-cpp[NVC_ATL_COM#7](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_3.cpp)]

   可以使用**IWebBrowser2**方法因为 ATL.h 文件中为您提供指向该接口的指针。

接下来，修改要调用的方法创建的 HTML 资源。 您将添加用于调用这些方法的三个按钮。  

#### <a name="to-modify-the-html-resource"></a>若要修改 HTML 资源

1. 在解决方案资源管理器，双击要显示的 HTML 资源的.htm 文件。

   检查 HTML，尤其是对外部 Windows 调度方法调用。 HTML 调用项目的`OnClick`方法和参数指示该控件的正文 (`theBody`) 和要分配的颜色 ("`red`")。 方法调用后面的文本是按钮显示的标签。

2. 添加另一个`OnClick`方法，仅更改颜色。 例如：

    ```html
    <br>
    <br>
    <BUTTON onclick='window.external.OnClick(theBody, "white");'>Refresh</BUTTON>
    ```

   此方法将创建一个按钮，标记为**刷新**，用户可以单击以将控件返回到原始的白色背景。

3. 将调用添加到`HelloHTML`方法创建。 例如：

    ```html
    <br>  
    <br>  
    <BUTTON onclick='window.external.HelloHTML();'>HelloHTML</BUTTON>  
    ```

   此方法将创建一个按钮，标记为**HelloHTML**，用户可以单击以显示`HelloHTML`消息框。

现在可以生成并[测试修改后的 DHTML 控件](../atl/testing-the-modified-atl-dhtml-control.md)。

## <a name="see-also"></a>请参阅

[支持 DHTML 控件](../atl/atl-support-for-dhtml-controls.md)
