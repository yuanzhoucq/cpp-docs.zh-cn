---
title: 将在网页上 (ATL 教程，第 7) 控件置于 |Microsoft Docs
ms.custom: get-started-article
ms.date: 09/27/2018
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 50dc4c95-c95b-4006-b88a-9826f7bdb222
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 052c6fa80b222a077fb41d861a4ea234f64073ec
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/05/2018
ms.locfileid: "48821603"
---
# <a name="putting-the-control-on-a-web-page-atl-tutorial-part-7"></a>将控件置于网页上（ATL 教程，第 7 部分）

您的控件现已完成。 若要查看的控件工作在实际情况下，将其放在网页上。 在您定义控件时创建一个包含控件的 HTML 文件。 打开 PolyCtl.htm 文件从**解决方案资源管理器**，可以看到您在网页上的控件。

在此步骤中，会将功能添加到控件和脚本 Web 页后，可以对事件做出响应。 您还将修改控件以使 Internet 资源管理器知道该控件可安全执行脚本。

## <a name="adding-new-functionality"></a>添加新功能

### <a name="to-add-control-features"></a>若要添加控制功能

1. 打开 PolyCtl.cpp 并将以下代码：

    ```cpp
    if (PtInRegion(hRgn, xPos, yPos))
        Fire_ClickIn(xPos, yPos);
    else
        Fire_ClickOut(xPos, yPos);
    ```

    替换为

    ```cpp
    short temp = m_nSides;
    if (PtInRegion(hRgn, xPos, yPos))
    {
        Fire_ClickIn(xPos, yPos);
        put_Sides(++temp);
    }
    else
    {
        Fire_ClickOut(xPos, yPos);
        put_Sides(--temp);
    }
    ```

现在，该形状将添加或删除边，具体取决于您单击的位置。

## <a name="scripting-the-web-page"></a>脚本编写 Web 页

该控件不执行任何操作尚未，因此，请更改网页以响应您发送的事件。

### <a name="to-script-the-web-page"></a>若要给网页编写脚本

1. 打开 PolyCtl.htm 并选择 HTML 视图。 将以下行添加到 HTML 代码。 应将它们添加后`</OBJECT>`之前`</BODY>`。

    ```html
    <SCRIPT LANGUAGE="VBScript">
    <!--
        Sub PolyCtl_ClickIn(x, y)
            MsgBox("Clicked (" & x & ", " & y & ") - adding side")
        End Sub
        Sub PolyCtl_ClickOut(x, y)
            MsgBox("Clicked (" & x & ", " & y & ") - removing side")
        End Sub
    -->
    </SCRIPT>
    ```

1. 保存 HTM 文件。

您已添加一些 VBScript 代码，从控件获取 Sides 属性，并会边数增加 1，如果在控件内单击。 如果在控件外单击，您会减少一个边数。

## <a name="indicating-that-the-control-is-safe-for-scripting"></a>该值指示控件为可安全执行脚本

可以在 Internet Explorer 中查看与该控件的网页或详细信息为方便起见，使用 Visual c + + 中内置的 Web 浏览器视图。 若要查看您的控件在 Web 浏览器视图中，右键单击 PolyCtl.htm，然后单击**在浏览器中的查看**。

> [!NOTE]
> 如果控件不可见，知道某些浏览器，需要运行 ActiveX 控件的设置调整。 请参阅有关如何启用 ActiveX 控件的浏览器的文档。

根据您当前的 Internet Explorer 安全设置，可能会收到一条安全警告对话框，其内容控件可能不安全的脚本，并可能造成损害。 例如，如果有一个控件，显示一个文件，但也有`Delete`删除了某个文件的方法，安全的情况是，只需在页面上查看它即可。 它将是不安全的可编写脚本，但是，因为有人可能调用`Delete`方法。

> [!IMPORTANT]
> 对于本教程中，可以更改 Internet Explorer 以运行未标记为安全的 ActiveX 控件中的安全设置。 在控制面板中，单击**互联**然后单击**安全**更改相应设置。 完成本教程后，将您的安全设置更改回其原始状态。

以编程方式发出警报，Internet Explorer，它不需要显示此特定控件的安全警报对话框。 为此可以使用`IObjectSafety`接口，并且 ATL 提供的此接口的类中实现[IObjectSafetyImpl](../atl/reference/iobjectsafetyimpl-class.md)。 若要将接口添加到您的控件，添加`IObjectSafetyImpl`到继承类列表并在 COM 映射中为其添加一个条目。

### <a name="to-add-iobjectsafetyimpl-to-the-control"></a>将 IObjectSafetyImpl 添加到控件

1. 将以下行添加到 PolyCtl.h 中继承类的列表的末尾和到上一行添加一个逗号：

    [!code-cpp[NVC_ATL_Windowing#62](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_1.h)]

1. 将以下行添加到 PolyCtl.h 中的 COM 映射：

    [!code-cpp[NVC_ATL_Windowing#63](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_2.h)]

## <a name="building-and-testing-the-control"></a>生成和测试控件

生成控件。 完成生成后中, 再次在浏览器视图中打开 PolyCtl.htm。 此时，Web 页应直接而不显示**安全警报**对话框。 单击多边形; 的内部边数增加 1。 单击多边形的外部以减少边数。

[返回到步骤 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)

## <a name="next-steps"></a>后续步骤

ATL 教程到此结束。 有关指向 ATL 更多信息，请参阅[ATL 起始页](../atl/active-template-library-atl-concepts.md)。

## <a name="see-also"></a>请参阅

[教程](../atl/active-template-library-atl-tutorial.md)
