---
title: 添加控件（ATL 教程，第 2 部分）
ms.custom: get-started-article
ms.date: 08/19/2019
ms.assetid: c9575a75-1064-41f1-9697-7aada560c669
ms.openlocfilehash: b7952f42b24c4211a2c44ea71fd17e4f65c3421a
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630702"
---
# <a name="adding-a-control-atl-tutorial-part-2"></a>添加控件（ATL 教程，第 2 部分）

在此步骤中, 你将向项目中添加一个控件、生成该控件, 然后在网页上对其进行测试。

## <a name="procedures"></a>过程

### <a name="to-add-an-object-to-an-atl-project"></a>向 ATL 项目添加对象

1. 在“解决方案资源管理器”中，右键单击“`Polygon`”项目。

1. 指向快捷菜单上的 "**添加**", 然后单击子菜单中的 "**新建项**"。

    “添加新项”对话框随即出现。 左侧的树结构中列出了不同的对象类别。

1. 单击 " **ATL** " 文件夹。

1. 从右侧的模板列表中, 选择 " **ATL 控件**"。 单击 **添加**。 **ATL 控件**向导将打开, 您可以配置控件。

1. 键入`PolyCtl`作为短名称, 并注意其他字段自动完成。 不要单击 "**完成**", 因为你必须进行更多更改。

**ATL 控件**向导的 "**名称**" 页包含下列字段:

|字段|内容|
|-----------|--------------|
|**短名称**|为控件输入的名称。|
|**类**|为C++实现控件而创建的类名。|
|**.h 文件**|为包含C++类的定义而创建的文件。|
|**.cpp 文件**|为包含C++类的实现而创建的文件。|
|**CoClass**|此控件的组件类的名称。|
|**Interface**|接口的名称, 控件将在该接口上实现其自定义方法和属性。|
|类型|控件的说明。|
|**编程 ID**|可用于查找控件 CLSID 的可读名称。|

你将在**ATL 控件**向导中找到多个其他设置。

### <a name="to-enable-support-for-rich-error-information-and-connection-points"></a>启用对丰富的错误信息和连接点的支持

1. 单击 "**选项**" 以打开 "**选项**" 页。

1. 选中 "**连接点**" 复选框。 此选项将为 IDL 文件中的输出接口创建支持。

你还可以添加接口以扩展控件的功能。

### <a name="to-extend-the-controls-functionality"></a>扩展控件的功能

1. 单击 "**接口**" 打开 "**接口**" 页。

1. 选择`IProvideClassInfo2`并单击**向上**箭头, 将其移动到**受支持**的列表中。

1. 选择`ISpecifyPropertyPages`并单击**向上**箭头, 将其移动到**受支持**的列表中。

还可以使控件可*插入*, 这意味着可将其嵌入到支持嵌入对象 (如 Excel 或 Word) 中的应用程序。

### <a name="to-make-the-control-insertable"></a>使控件可插入

1. 单击 "**外观**" 以打开 "**外观**" 页。

1. 选中 "**插入**" 复选框。

对象显示的多边形将具有纯色填充颜色, 因此必须添加`Fill Color`常用属性。

### <a name="to-add-a-fill-color-stock-property-and-create-the-control"></a>添加 "填充颜色" 常用属性并创建控件

1. 单击 "**常用属性**" 以打开 "**常用属性**" 页。

1. 在 "**不支持**" 下, 向下滚动可能的常用属性列表。 选择`Fill Color`并单击**向上**箭头, 将其移动到**受支持**的列表中。

1. 选择“完成”。

当向导创建控件时, 将发生若干代码更改和文件添加。 创建下列文件:

|文件|描述|
|----------|-----------------|
|PolyCtl.h|包含C++类`CPolyCtl`的大部分实现。|
|PolyCtl.cpp|包含的`CPolyCtl`其余部分。|
|PolyCtl.rgs|一个文本文件, 其中包含用于注册控件的注册表脚本。|
|PolyCtl.htm|包含对新创建的控件的引用的网页。|

该向导还会更改以下代码:

- 向预编译标头文件添加语句,以包含支持控件所需的ATL文件。`#include`

- 更改多边形 .idl 以包括新控件的详细信息。

- 将新控件添加到多边形 .cpp 中的对象映射。

现在, 可以生成控件以查看其操作。

## <a name="building-and-testing-the-control"></a>生成和测试控件

### <a name="to-build-and-test-the-control"></a>生成并测试控件

1. 在 "**生成**" 菜单上, 单击 "**生成多边形**"。

    控件完成生成后, 在**解决方案资源管理器**中右键单击 "polyctl.htm", 然后选择 **"在浏览器中查看"** 。 将显示包含控件的 HTML 网页。 应该会看到一个页面, 其中标题为 "用于对象 Polyctl.htm 的 ATL 8.0 测试页" 和控件, 即 "Polyctl.htm" 文本。

> [!NOTE]
> 如果该控件不可见, 则知道某些浏览器需要设置调整才能运行 ActiveX 控件。 请参阅浏览器文档, 了解如何启用 ActiveX 控件。

> [!NOTE]
> 完成本教程时, 如果收到一条错误消息, 指出无法创建 DLL 文件, 请关闭 Polyctl.htm 文件和 ActiveX 控件测试容器, 并再次生成解决方案。 如果仍无法创建 DLL, 请重新启动计算机, 或者在使用终端服务时注销。

接下来, 将自定义属性添加到控件。

[返回到步骤 1](../atl/creating-the-project-atl-tutorial-part-1.md)&#124; [到步骤 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md)

## <a name="see-also"></a>请参阅

[教程](../atl/active-template-library-atl-tutorial.md)
