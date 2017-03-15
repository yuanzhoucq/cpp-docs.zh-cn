---
title: "添加控件（ATL 教程，第 2 部分） | Microsoft Docs"
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
ms.assetid: c9575a75-1064-41f1-9697-7aada560c669
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 添加控件（ATL 教程，第 2 部分）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在此步骤中，您将添加一个控件添加到项目中，生成控件，然后在网页上测试空间。  
  
## 过程  
  
#### 在 ATL 项目中添加一个项目  
  
1.  在“类视图”中，右击 Polygon 项目。  
  
2.  指向快捷菜单上的“添加”，并点击子菜单中的“类”。  
  
     出现“添加类”对话框。  不同的对象类别列在左侧的树状结构中。  
  
3.  单击“ATL”文件夹。  
  
4.  从右侧的模板列表中选择“ATL 控件”。  单击**“添加”**。  ATL 控件向导将打开，您可以配置控件。  
  
5.  键入 `PolyCtl` 为短名称，请注意其他字段是自动完成的。  现在还不要单击“完成”，因为您需要做出一些更改。  
  
 ATL 控件向导的“名称”页包含以下字段：  
  
|字段|内容|  
|--------|--------|  
|**简称**|输入的控件的名称。|  
|**类**|创建的 C\+\+ 类名实现控件。|  
|**.h 文件**|创建用于包含 C\+\+ 类定义的文件。|  
|**.cpp 文件**|创建用于包含 C\+\+ 类实现的文件。|  
|**组件类**|该控件的组件类名称。|  
|**接口**|控件将实现其自定义方法和属性的接口名称。|  
|**类型**|关于控件的说明。|  
|**ProgID**|可用于查找控件的 CLSID 的可读名称。|  
  
 您必须在 ATL 控制向导中进行若干额外的设置。  
  
#### 启用对丰富的错误信息和连接点的支持  
  
1.  单击“选项”以打开“选项”页面。  
  
2.  选择“连接点”复选框。  这将为 IDL 文件的一个输出接口创建支持。  
  
 也可让控件可插入，这意味着可将其嵌入支持嵌入对象的应用程序（如 Excel 或 Word）。  
  
#### 使控件可插入  
  
1.  单击“外观”以打开“外观”**Appearance**页面。  
  
2.  选中“可插入”复选框。  
  
 对象公开的多边形将具有固定的填充颜色，因此，您必须添加 `Fill Color` 常见属性。  
  
#### 添加“填充颜色”常用属性和创建控件  
  
1.  单击“常用属性”以打开“常用属性”页面。  
  
2.  在“不受支持”下，向下滚动可能常用属性列表。  双击 `Fill Color` 将其移动到“支持的”列表。  
  
3.  这将完成控件选项。  单击“完成”。  
  
 向导创建控件时，发生了某些代码更改和文件添加。  创建了以下文件：  
  
|文件|描述|  
|--------|--------|  
|PolyCtl.h|包含 C\+\+ 类 `CPolyCtl`的大部分实现。|  
|PolyCtl.cpp|包含 `CPolyCtl` 的剩余部分。|  
|PolyCtl.rgs|包含用来注册控件的注册表脚本的文本文件。|  
|PolyCtl.htm|包含对新创建的控件的引用的网页。|  
  
 该向导还可执行以下代码更改：  
  
-   将 `#include` 语句添加到 stdafx.h 和 stdafx.cpp 文件中，以包含支持控件所需的 ATL 文件。  
  
-   更改 Polygon.idl 使其包含新控件的详细信息。  
  
-   将新控件添加到 Polygon.cpp 中的对象映射中。  
  
 现在您可以生成控件以在实际运行中了解它。  
  
## 生成和测试控件  
  
#### 生成并测试控件  
  
1.  在“生成”菜单上，单击“生成多边形”。  
  
     控件生成完成后，右击“解决方案资源管理器”中的 PolyCtl.htm 并选择“在浏览器中查看”。  将会显示包含控件的 HTML 网页。  您应该看到具有标题“对象 PolyCtl 的 ATL 8.0 测试页”和文本 **PolyCtl** 的页。  这是您的控件。  
  
> [!NOTE]
>  完成本教程时，如果您在无法创建 DLL 该文件时收到错误消息，请关闭 PolyCtl.htm 文件和 Activex 控件测试容器并重新生成解决方案。  如果仍无法创建 DLL，请重新启动计算机或注销（如果使用的是终端服务）。  
  
 然后，您将向控件添加自定义属性。  
  
 [返回步骤 1](../atl/creating-the-project-atl-tutorial-part-1.md) &#124; [转到步骤 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md)  
  
## 请参阅  
 [教程](../atl/active-template-library-atl-tutorial.md)