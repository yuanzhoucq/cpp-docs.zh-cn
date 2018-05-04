---
title: 添加控件 (ATL 教程，第 2 部分) |Microsoft 文档
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c9575a75-1064-41f1-9697-7aada560c669
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d3b8c7eb59579363ce3580c7319b80be2557a30d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="adding-a-control-atl-tutorial-part-2"></a>添加控件（ATL 教程，第 2 部分）
在此步骤中，将控件添加到你的项目，生成它，并在网页上对其进行测试。  
  
## <a name="procedures"></a>过程  
  
#### <a name="to-add-an-object-to-an-atl-project"></a>将对象添加到 ATL 项目  
  
1.  在类视图中，右键单击多边形项目。  
  
2.  指向**添加**快捷菜单，然后单击**新项**的子菜单中。  
  
     “添加新项”对话框随即出现。 在左侧的树状结构列出了不同的对象类别。  
  
3.  单击**ATL**文件夹。  
  
4.  从右侧的模板列表中，选择**ATL 控件**。 单击 **添加**。 ATL 控件向导将打开，并且可以配置该控件。  
  
5.  类型`PolyCtl`短名称以及其他字段将自动完成的注意。 不要单击**完成**尚未，因为你必须进行一些更改。  
  
 ATL 控件向导**名称**页包含以下字段：  
  
|字段|内容|  
|-----------|--------------|  
|**短名称**|输入控件的名称。|  
|**类**|创建实现控件的 c + + 类名称。|  
|**.h 文件**|创建包含 c + + 类定义的文件。|  
|**.cpp 文件**|创建包含 c + + 类的实现的文件。|  
|**组件类**|对于此控件的组件类的名称。|  
|**Interface**|控件将在其实现其自定义的方法和属性的接口的名称。|  
|**Type**|该控件的说明。|  
|**ProgID**|可用于查找控件的 CLSID 可读名称。|  
  
 你必须在 ATL 控件向导进行多个附加设置。  
  
#### <a name="to-enable-support-for-rich-error-information-and-connection-points"></a>启用支持丰富的错误信息和连接点  
  
1.  单击**选项**以打开**选项**页。  
  
2.  选择**连接点**复选框。 这将在 IDL 文件中创建的传出接口的支持。  
  
 此外可以使控件可插入，但这意味着它可以嵌入到支持嵌入的对象，如 Excel 或 Word 的应用程序。  
  
#### <a name="to-make-the-control-insertable"></a>若要使控件可插入  
  
1.  单击**外观**以打开**外观**页。  
  
2.  选择**可插入**复选框。  
  
 多边形显示由该对象将具有纯色填充颜色，因此你必须添加`Fill Color`常用属性。  
  
#### <a name="to-add-a-fill-color-stock-property-and-create-the-control"></a>若要添加的填充颜色常用属性，创建控件  
  
1.  单击**常用属性**以打开**常用属性**页。  
  
2.  下**不支持**，向下滚动可能常用属性的列表。 双击`Fill Color`将其移至**支持**列表。  
  
3.  这将完成该控件的选项。 单击 **“完成”**。  
  
 在向导创建控件，将发生多个代码更改和文件添加。 创建以下文件：  
  
|文件|描述|  
|----------|-----------------|  
|PolyCtl.h|包含大多数 c + + 类的实现`CPolyCtl`。|  
|PolyCtl.cpp|包含的其余部分`CPolyCtl`。|  
|PolyCtl.rgs|包含用于注册此控件的注册表脚本的文本文件。|  
|PolyCtl.htm|网页包含对新创建的控件的引用。|  
  
 向导还执行以下代码更改：  
  
-   添加`#include`语句包括 ATL 的 stdafx.h 和 stdafx.cpp 文件所需的支持控件文件。  
  
-   Polygon.idl 已更改，以包括新控件的详细信息。  
  
-   到 Polygon.cpp 中的对象映射中添加新控件。  
  
 现在你可以生成该控件以查看在操作中。  
  
## <a name="building-and-testing-the-control"></a>生成和测试控件  
  
#### <a name="to-build-and-test-the-control"></a>生成并测试控件  
  
1.  上**生成**菜单上，单击**生成多边形**。  
  
     完成该控件后生成，右键单击在 PolyCtl.htm**解决方案资源管理器**和选择**用浏览器查看**。 将显示包含控件的 HTML 网页。 你应看到"ATL 对象 PolyCtl 8.0 测试页"的标题和文本页**PolyCtl**。 这是您的控件。  
  
> [!NOTE]
>  完成本教程中，如果你收到一条错误消息不能在其中创建 DLL 文件后，关闭 PolyCtl.htm 文件和 ActiveX 控件测试容器，并再次生成解决方案。 如果您仍无法创建 DLL，重新启动计算机或注销 （如果你使用的终端服务）。  
  
 接下来，你将向控件添加自定义属性。  
  
 [返回到步骤 1](../atl/creating-the-project-atl-tutorial-part-1.md) &#124; [到步骤 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md)  
  
## <a name="see-also"></a>请参阅  
 [教程](../atl/active-template-library-atl-tutorial.md)

