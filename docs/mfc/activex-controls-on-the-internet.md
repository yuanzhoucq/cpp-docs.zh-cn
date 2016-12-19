---
title: "Internet 上的 ActiveX 控件 | Microsoft Docs"
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
  - "ActiveX 控件 [C++], 创建"
  - "ActiveX 控件 [C++], Internet"
  - "使用 ActiveX 控件下载数据"
  - "Internet 应用程序 [C++], ActiveX 控件"
  - "网络 [C++], 使用 ActiveX 控件下载"
  - "OLE 控件 [C++], 升级到 ActiveX"
ms.assetid: 7ab943c8-2022-41df-9065-d629b616eeec
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Internet 上的 ActiveX 控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ActiveX 控件是 OLE 控件指定的更新版本。  控件是开发的可在多种不同的容器中处理可编程的软件组件主结构，其中包括 Internet 上的 COM 支持 Web 浏览器。  所有 ActiveX 控件是 Internet 控件，可将其功能添加到文档或活动是网页的一部分。  使用脚本，网页上的控件可以互相通信。  
  
 ActiveX 控件不会被限制到 Internet。  只要，控件支持必需的接口，该容器 ActiveX 控件也可以用于任何容器。  
  
 **ActiveX 控件有以下优点，包括：**  
  
-   少量必需的接口与早期 OLE 控件。  
  
-   能力是无窗口和始终处于就地活动状态。  
  
 **若要是 ActiveX 控件，控件必须：**  
  
-   支持 **IUnknown** 接口。  
  
-   是 COM 对象。  
  
-   导出 **DLLRegisterServer** 和 **DLLUnRegisterServer**。  
  
-   支持附加接口需要用于功能。  
  
## 使现有控件 Internet 友好  
 设计在 Internet 环境将好工作的控件对 Internet 的相对较低传输率需要注意事项。  可以使用现有控件；但是，也应该采取使代码大小更小并使控件属性异步下载的步骤。  
  
 若要提高控件的性能，请遵循对效率注意事项进行这些提示：  
  
-   实现中介绍的技术文章 [ActiveX 控件：优化](../mfc/mfc-activex-controls-optimization.md)。  
  
-   考虑控件如何实例化。  
  
-   异步；请勿保存其他程序。  
  
-   下载在小块的数据。  
  
     当下载大流 \(例如位图或视频数据时，请在协作与容器下访问控制数据。  检索数据增量或进度情况下，共同使用还检索为其他数据控件一样。  代码还可以异步下载。  
  
-   代码下载和属性位于背景。  
  
-   成为激活尽快的用户界面。  
  
-   考虑不可变数据的存储方式，属性和大数据 Blob \(如位图图像或视频数据。  
  
     带有数量的持久性数据控件，如大位图或 AVI 文件，需要对下载方法进行仔细考虑。  在后台，当控件检索数据时，或页面文档可以尽快变为可见，并允许用户与页面交互。  
  
-   编写有效的例程使编码规范和运行时。  
  
     小按钮和标签控件，仅使用某些字节的持久性数据适用于，Internet 环境并可很好地发挥作用。在浏览器中。  
  
-   考虑进行通信。容器。  
  
     通知容器在异步下载的进度，包含用户可以启动与页面交互，并且，下载完成的。  容器可以查看进度 \(如完成百分比\) 给用户。  
  
-   考虑控件如何在客户端计算机上注册。  
  
## 创建 一个新的MFC ActiveX 控件  
 在创建新的控件使用应用程序向导，则可以选择启用异步名字对象以及其他优化的支持。  若要添加支持到下载中控制属性异步，执行以下步骤：  
  
#### 若要创建项目使用 MFC ActiveX 控件向导  
  
1.  在 **文件**菜单上，单击 `New`。  
  
2.  从 Visual C\+\+ 项目中选择 **MFC ActiveX 控件向导** 并命名项目。  
  
3.  在 **控件设置** 页中，选择 **异步加载属性 \(L\)**。  选择此选项设置就绪状态属性和就绪状态更改事件了。  
  
     还可以选择其他优化，例如 **无窗口激活 \(S\)**，在 [ActiveX 控件：优化](../mfc/mfc-activex-controls-optimization.md)中描述。  
  
4.  关闭**“完成”**创建项目。  
  
#### 创建从 CDataPathProperty 派生的类  
  
1.  创建从 `CDataPathProperty` 导出的新类。  
  
2.  在包含控件的标头文件的每个源文件，请在它之前添加此类的头文件。  
  
3.  在此类中，重写 `OnDataAvailable`。  此函数调用，每当数据用于显示中可用。  在数据变得可用，可以通过进度呈现它处理它您选择的任何方式。例如，  
  
     下面的代码是在编辑控件显示进度的摘要数据的简单示例。  请注意使用 **BSCF\_FIRSTDATANOTIFICATION** 标志清除编辑控件。  
  
     [!code-cpp[NVC_MFCActiveXControl#1](../mfc/codesnippet/CPP/activex-controls-on-the-internet_1.cpp)]  
  
     注意必须包括使用的 AFXCMN.H `CListCtrl` 类。  
  
4.  当控件的总体状态转换 \(例如，从到交互式初始化或加载的用户\)，请调用 `COleControl::InternalSetReadyState`。  如果控件只具有数据访问权。属性，可以添加到的 **BSCF\_LASTDATANOTIFICATION** 代码通知容器下载完成。  例如：  
  
     [!code-cpp[NVC_MFCActiveXControl#2](../mfc/codesnippet/CPP/activex-controls-on-the-internet_2.cpp)]  
  
5.  重写 `OnProgress`。  在 `OnProgress`，请将显示的数字显示沿当前下载进度的最大大小和数量为。  可以使用这些数字显示完成状态 \(如从中百分用户。  
  
 下一个过程将属性添加到控件使用派生的类。  
  
#### 添加属性  
  
1.  在"类视图" 中，右击位于库节点之下的接口并选择 **添加**，然后单击 "添加属性"。  这将启动 **添加属性向导**。  
  
2.  在 **添加属性向导**中，选择 **Set\/Get Methods** 单选按钮，键入 **属性名**，例如，EditControlText，并选择作为 BSTR **属性类型**。  
  
3.  单击**“完成”**。  
  
4.  声明 `CDataPathProperty`的成员变量。对 ActiveX 控件类的派生类。  
  
     [!code-cpp[NVC_MFCActiveXControl#3](../mfc/codesnippet/CPP/activex-controls-on-the-internet_3.h)]  
  
5.  实现 **Get\/Set** 方法。  对于 **Get**，将返回字符串。  对于 `Set`，请加载属性并调用 `SetModifiedFlag`。  
  
     [!code-cpp[NVC_MFCActiveXControl#4](../mfc/codesnippet/CPP/activex-controls-on-the-internet_4.cpp)]  
  
6.  在 [DoPropExchange](../Topic/COleControl::DoPropExchange.md) 中，添加下列行：  
  
     [!code-cpp[NVC_MFCActiveXControl#5](../mfc/codesnippet/CPP/activex-controls-on-the-internet_5.cpp)]  
  
7.  重写属性通知的 [ResetData](../Topic/CDataPathProperty::ResetData.md) 通过将此行重置其控件：  
  
     [!code-cpp[NVC_MFCActiveXControl#6](../mfc/codesnippet/CPP/activex-controls-on-the-internet_6.cpp)]  
  
## 决定是否从 CDataPathProperty 或 CCachedDataPathProperty 派生  
 上面描述步骤从 `CDataPathProperty`派生的控件的属性。  这是一个很好的选择，如果您下载经常更改的实时数据，并且，对于您不需要保留所有数据，但是，只有当前值。  示例是一"股票行情自动收录器"控件。  
  
 您还可以通过从 `CCachedDataPathProperty`派生。  在这种情况下，请下载的数据在内存缓存文件。  这是一个好选择，例如如果需要保留所有下载的数据\)，呈现箭头位图的控件。  在这种情况下，类包含数据的成员变量：  
  
 `CMemFile m_Cache;`  
  
 在 ActiveX 控件类，可以使用 `OnDraw` 中此内存映射文件来显示数据。  在 ActiveX 控件 `CCachedDataPathProperty`派生类，请重写 `OnDataAvailable` 成员函数并且在调用基类实现后无效，控件。  
  
 [!code-cpp[NVC_MFCActiveXControl#7](../mfc/codesnippet/CPP/activex-controls-on-the-internet_7.cpp)]  
  
## 异步下载数据使用 ActiveX 控件  
 网络应完成异步下载数据。  这样做的优点是，则大量数据传输，或者连接很慢，不会下载过程阻挠客户端上的其他进程。  
  
 异步名字对象提供了一种异步下载数据网络。  在异步名字对象的一次读取操作将立即返回，因此，即使一操作尚未完成。  
  
 例如，在中，如果仅为 10 字节，并且读取可在 1K 文件异步调用，读取不阻止，但返回与现在可用的 10 字节。  
  
 使用 `CAsyncMonikerFile` 类，您需要实现 [异步名字对象](../mfc/asynchronous-monikers-on-the-internet.md)。  但是，ActiveX 控件可以使用 `CDataPathProperty` 类，从 `CAsyncMonikerFile`中派生，这样有助于实现异步控件属性。  
  
 ASYNDOWN 示例演示如何设置一异步循环使用计时器读取数据。  在“详细介绍如何 ASYNDOWN 知识库文章：AsyncDown 演示异步数据下载”\(Q177244\) 并可以从 Microsoft 下载中心下载。\(有关下载的更多信息可以从 Microsoft 下载中心的文件，请参见联机文章“How to obtain Microsoft 服务的支持文件”\(Q119591\) 在 Microsoft 知识库。\)知识库文章位于 MSDN Library CD\-ROM中或 [http:\/\/support.microsoft.com\/support\/](http://support.microsoft.com/support) 上。  
  
 在 ASYNDOWN 的基本技术是将 **CDataPathProperty::OnDataAvailable** 中的计时器指示数据可用时。  在计时器接收消息时，应用程序编写数据 128 字节块并填充编辑控件。  如果数据不可用，则计时器消息已处理时，计时器会关闭。  如果更多数据迟到，`OnDataAvailable` 启动计时器。  
  
## 显示网页上的控件  
 这是一对象标记和特性的示例插入的控件在网页上。  
  
 `<OBJECT`  
  
 `CLASSID="clsid:FC25B780-75BE-11CF-8B01-444553540000"`  
  
 `CODEBASE="/ie/download/activex/iechart.ocx"`  
  
 `ID=chart1`  
  
 `WIDTH=400`  
  
 `HEIGHT=200`  
  
 `ALIGN=center`  
  
 `HSPACE=0`  
  
 `VSPACE=0`  
  
 `>`  
  
 `<PARAM NAME="BackColor" value="#ffffff">`  
  
 `<PARAM NAME="ForeColor" value="#0000ff">`  
  
 `<PARAM NAME="url" VALUE="/ie/controls/chart/mychart.txt">`  
  
 `</OBJECT>`  
  
## 更新现有的 OLE 控件使用新的 ActiveX 控件功能  
 如果 OLE 控件使用 Visual C\+\+ 创建在版本 4.2 之前，您可以拍摄改进其性能和增强其功能的步骤。  对于常规讨论这些更改的详细讨论，请参见 [ActiveX 控件：优化](../mfc/mfc-activex-controls-optimization.md)。  
  
 如果添加异步的属性支持到现有控件，则需要添加就绪状态属性和 `ReadyStateChange` 事件。  在控件的构造函数中，添加：  
  
 [!code-cpp[NVC_MFCActiveXControl#8](../mfc/codesnippet/CPP/activex-controls-on-the-internet_8.cpp)]  
  
 将更新就绪状态，代码通过调用 [COleControl::InternalSetReadyState](../Topic/COleControl::InternalSetReadyState.md)下载。  您可以调用 `InternalSetReadyState` 的一个位置是从 `CDataPathProperty`重写 `OnProgress` 派生类。  
  
 然后，按照 [创建一个新的 ActiveX 控件](#_core_how_do_i_create_a_new_activex_control.3f)的步骤。  
  
## 请参阅  
 [MFC Internet 编程任务](../mfc/mfc-internet-programming-tasks.md)   
 [MFC Internet 编程基础知识](../mfc/mfc-internet-programming-basics.md)