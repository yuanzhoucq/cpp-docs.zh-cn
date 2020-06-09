---
title: Internet 上的 ActiveX 控件
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX controls [MFC], creating
- ActiveX controls [MFC], Internet
- downloading data with ActiveX controls
- OLE controls [MFC], upgrading to ActiveX
- Internet applications [MFC], ActiveX controls
- networks [MFC], downloading with ActiveX controls
ms.assetid: 7ab943c8-2022-41df-9065-d629b616eeec
ms.openlocfilehash: f06a6f6f71e922163fd95c59836c50b88b05ed3a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616477"
---
# <a name="activex-controls-on-the-internet"></a>Internet 上的 ActiveX 控件

ActiveX 控件是 OLE 控件规范的更新版本。

>[!IMPORTANT]
> ActiveX 是一种不能用于新开发的旧技术。 有关详细信息，请参阅[ActiveX 控件](activex-controls.md)。

控件是开发可在各种不同容器（包括 Internet 上的 COM 感知 Web 浏览器）中使用的可编程软件组件的主要体系结构。 任何 ActiveX 控件都可以是 Internet 控件，并且可将其功能添加到活动文档或成为网页的一部分。 网页上的控件可以使用脚本互相通信。

ActiveX 控件不受 Internet 限制。 ActiveX 控件还可在任何容器中使用，前提是控件支持容器所需的接口。

**ActiveX 控件有以下优点，包括：**

- 需要的接口比以前的 OLE 控件少。

- 能够处于无窗口状态并始终处于就地活动状态。

**若要成为 ActiveX 控件，控件必须：**

- 支持 `IUnknown` 接口。

- 是 COM 对象。

- 导出**DLLRegisterServer**和**DLLUnRegisterServer**。

- 支持功能所需的其他接口。

## <a name="making-your-existing-controls-internet-friendly"></a>使现有控件支持 Internet

设计在 Internet 环境下正常运行的控件需要考虑 Internet 上相对较低的转换率。 你可以使用现有控件；但是，你应采取下列步骤使你的代码大小更小以及使你的控件属性能够异步下载。

若要提高控件的性能，请遵循下列有关效率注意事项的提示：

- 实现[ActiveX 控件：优化](mfc-activex-controls-optimization.md)一文中所述的方法。

- 考虑如何实例化控件。

- 异步；请勿阻止其他程序。

- 下载小块数据。

   下载位图或视频数据等大型流时，请与容器合作异步访问控件的数据。 以增量方式或渐进式检索数据，与还可能检索数据的其他控件协作。 代码还可以异步下载。

- 下载后台中的代码和属性。

- 尽可能快地处于用户界面活动状态。

- 考虑存储永久数据（属性和大型数据 Blob（如位图图像或视频数据））的方式。

   具有大量永久数据（如大型位图或 AVI 文件）的控件需要特别关注下载方式。 文档或页面可尽可能变得可见，并且允许用户在控件检索背景数据时与页面交互。

- 编写有效的例程以缩减代码大小和运行时间。

   只具有少量字节永久数据的小按钮和标签控件适用于在 Internet 环境中使用并且将在浏览器中运行良好。

- 考虑将进度传送到容器。

   将异步下载的进度通知给容器，包括用户可开始与页面交互的时间以及下载完成的时间。 容器可以将进度（如完成百分比）显示给用户。

- 考虑在客户端计算机上注册控件的方式。

## <a name="creating-a-new-activex-control"></a>创建新的 ActiveX 控件

在使用应用程序向导创建新的控件时，您可选择为异步名字对象以及其他优化启用支持。 若要添加支持以异步下载控件属性，请执行下列步骤：

#### <a name="to-create-your-project-using-the-mfc-activex-control-wizard"></a>使用 MFC ActiveX 控件向导创建项目

1. 单击 "**文件**" 菜单上的 "**新建**"。

1. 从 Visual Studio c + + 项目中选择 " **MFC ActiveX 控件向导**" 并命名你的项目。

1. 在 "**控件设置**" 页上，选择 "**异步加载属性**"。 选择此选项将为您设置就绪状态属性和就绪状态更改事件。

   还可以选择其他优化，如 " [ActiveX 控件：优化](mfc-activex-controls-optimization.md)" 中所述的 "**无窗口激活**"。

1. 选择“完成”以创建项目  。

#### <a name="to-create-a-class-derived-from-cdatapathproperty"></a>创建派生自 CDataPathProperty 的类

1. 创建派生自 `CDataPathProperty` 的类。

1. 在包含控件头文件的每个源文件中，请在此类之前为它添加头文件。

1. 在此类中，重写 `OnDataAvailable`。 将在数据可显示时调用此函数。 在数据变得可用后，您可以通过选择的任何方式（例如，逐渐呈现的方式）处理数据。

   下面的代码摘要是在编辑控件中逐渐显示数据的简单示例。 请注意，使用标志**BSCF_FIRSTDATANOTIFICATION**清除编辑控件。

   [!code-cpp[NVC_MFCActiveXControl#1](codesnippet/cpp/activex-controls-on-the-internet_1.cpp)]

   请注意，您必须包括 AFXCMN.H 以使用 `CListCtrl` 类。

1. 当控件的整体状态发生更改（例如，从正在加载到已初始化或用户交互），请调用 `COleControl::InternalSetReadyState`。 如果控件只有一个数据路径属性，则可以在**BSCF_LASTDATANOTIFICATION**上添加代码以通知容器下载已完成。 例如：

   [!code-cpp[NVC_MFCActiveXControl#2](codesnippet/cpp/activex-controls-on-the-internet_2.cpp)]

1. 重写 `OnProgress`。 在 `OnProgress` 中，将为您传递一个显示最大范围的数以及一个显示当前下载还有多久完成的数。 您可以使用这些数字向用户显示完成百分比等状态。

下一个过程将属性添加到控件以使用刚刚派生的类。

#### <a name="to-add-a-property"></a>添加属性

1. 在**类视图**中，右键单击 "库" 节点下的接口并选择 "**添加**"，然后选择 "**添加属性**"。 这将启动 "**添加属性向导**"。

1. 在**添加属性向导**中，选择 "**设置/获取方法**" 单选按钮，键入**属性名称**（例如 EDITCONTROLTEXT），并选择 "BSTR" 作为**属性类型**。

1. 单击“完成”。

1. 将 `CDataPathProperty` 派生类的成员变量声明为 ActiveX 控件类。

   [!code-cpp[NVC_MFCActiveXControl#3](codesnippet/cpp/activex-controls-on-the-internet_3.h)]

1. 实现 `Get/Set` 方法。 对于 `Get` ，返回字符串。 对于 `Set`，将加载属性并调用 `SetModifiedFlag`。

   [!code-cpp[NVC_MFCActiveXControl#4](codesnippet/cpp/activex-controls-on-the-internet_4.cpp)]

1. 在[DoPropExchange](reference/colecontrol-class.md#dopropexchange)中，添加以下行：

   [!code-cpp[NVC_MFCActiveXControl#5](codesnippet/cpp/activex-controls-on-the-internet_5.cpp)]

1. 重写[ResetData](reference/cdatapathproperty-class.md#resetdata)以通知属性通过添加以下行来重置其控件：

   [!code-cpp[NVC_MFCActiveXControl#6](codesnippet/cpp/activex-controls-on-the-internet_6.cpp)]

## <a name="deciding-whether-to-derive-from-cdatapathproperty-or-ccacheddatapathproperty"></a>确定派生自 CDataPathProperty 还是 CCachedDataPathProperty

以上示例描述从 `CDataPathProperty` 派生控件的属性的步骤。 如果您下载频繁更改的实时数据，对于这些数据，您无需保留所有数据，但需仅保留当前值，则这是一个很好的选择。 示例是一个股票代码控件。

您还可以从 `CCachedDataPathProperty` 派生。 在此情况下，下载的数据将缓存在内存文件中。 如果您需要保留所有下载数据 — 例如，逐渐呈现位图的控件，则这是一个好选择。 在此情况下，类具有包含您的数据的成员变量：

`CMemFile m_Cache;`

在 ActiveX 控件类中，您可以使用 `OnDraw` 中的内存映射文件来显示数据。 在 ActiveX 控件 `CCachedDataPathProperty` 派生类中，重写成员函数 `OnDataAvailable` 并在调用基类实现之后使该控件无效。

[!code-cpp[NVC_MFCActiveXControl#7](codesnippet/cpp/activex-controls-on-the-internet_7.cpp)]

## <a name="downloading-data-asynchronously-using-activex-controls"></a>使用 ActiveX 控件异步下载数据

通过网络下载数据应异步完成。 这样做的优点是，如果传输大量数据或连接很慢，则下载进程将不会阻止客户端上的其他进程。

异步名字对象将提供通过网络异步下载数据的方式。 对异步名字对象的读取操作将立即返回，即使该操作尚未完成也是如此。

例如，如果仅提供 10 个字节并且对 1K 文件异步调用“读取”，则“读取”将不阻止，但与目前可用的 10 字节一起返回。

使用类实现[异步名字对象](asynchronous-monikers-on-the-internet.md) `CAsyncMonikerFile` 。 但是，ActiveX 控件可以使用 `CDataPathProperty` 类（派生自 `CAsyncMonikerFile`）帮助实现异步控件属性。

## <a name="displaying-a-control-on-a-web-page"></a>在网页上显示控件

以下是用于在网页上插入控件的对象标记和特性的示例。

```xml
<OBJECT
  CLASSID="clsid:FC25B780-75BE-11CF-8B01-444553540000"
  CODEBASE="/ie/download/activex/iechart.ocx"
  ID=chart1
  WIDTH=400
  HEIGHT=200
  ALIGN=center
  HSPACE=0
  VSPACE=0>
  <PARAM NAME="BackColor" value="#ffffff"/>
  <PARAM NAME="ForeColor" value="#0000ff"/>
  <PARAM NAME="url" VALUE="/ie/controls/chart/mychart.txt"/>
</OBJECT>
```

## <a name="updating-an-existing-ole-control-to-use-new-activex-control-features"></a>将现有 OLE 控件更新为使用新的 ActiveX 控件功能

如果 OLE 控件是使用 4.2 之前的 Visual C++ 版本创建的，则您可执行下列步骤来提高其性能并增强其功能。 有关这些更改的详细讨论，请参阅[ActiveX 控件：优化](mfc-activex-controls-optimization.md)。

如果要向现有控件添加异步属性支持，则需要添加就绪状态属性和 `ReadyStateChange` 事件。 在控件的构造函数中，添加：

[!code-cpp[NVC_MFCActiveXControl#8](codesnippet/cpp/activex-controls-on-the-internet_8.cpp)]

你将在通过调用[COleControl：： InternalSetReadyState](reference/colecontrol-class.md#internalsetreadystate)下载代码时更新就绪状态。 您可以调用 `InternalSetReadyState` 的一个位置是从 `OnProgress` 派生类的 `CDataPathProperty` 重写。

## <a name="see-also"></a>另请参阅

[MFC Internet 编程任务](mfc-internet-programming-tasks.md)<br/>
[MFC Internet 编程基础知识](mfc-internet-programming-basics.md)
