---
title: "升级现有 ActiveX 控件 | Microsoft Docs"
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
  - "ActiveX 控件 [C++], Internet"
  - "CAB 文件, 用于 ActiveX 控件"
  - "Internet 应用程序 [C++], ActiveX 控件"
  - "Internet 应用程序 [C++], 用于下载的包装代码"
  - "授权 ActiveX 控件"
  - "用于 Internet 控件的 LPK 文件"
  - "OLE 控件 [C++], 升级到 ActiveX"
  - "对于脚本编写和初始化而言是安全的（控件）"
  - "升级 ActiveX 控件"
ms.assetid: 4d12ddfa-b491-4f9f-a0b7-b51458e05651
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 升级现有 ActiveX 控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

现有的 ActiveX 控件 \(原来为 OLE控件\) 在 Internet 中可以使用，而无需修改。  但是，您可以修改控件以改善其性能。  在网页上使用控件时，还有其他注意事项。  必须在目标计算机或在 Internet 上下载 .ocx 文件和任何支持的文件。  这使代码大小和下载时成为一个重要注意事项。  下载像可以在签名的 .cab 文件中打包。  可以标记控件使其与用于脚本或初始化时同样安全。  
  
 本文讨论以下主题：  
  
-   [用于下载的包装代码](#_core_packaging_code_for_downloading)  
  
-   [标记脚本并初始化的一个安全控件](#_core_marking_a_control_safe_for_scripting_and_initializing)  
  
-   [发行许可证](#_core_licensing_issues)  
  
-   [签名代码](#_core_signing_code)  
  
-   [管理调色板](#_core_managing_the_palette)  
  
-   [Internet Explorer 浏览器安全级别和控件的行为](#_core_internet_explorer_browser_safety_levels_and_control_behavior)  
  
 也可以添加一优化，如 [ActiveX 控件：优化](../mfc/mfc-activex-controls-optimization.md)所述。  标记对象可用于异步下载属性和大 Blob，如 [Internet 上的 ActiveX 控件](../mfc/activex-controls-on-the-internet.md)所述。  
  
##  <a name="_core_packaging_code_for_downloading"></a> 用于下载的包装代码  
 有关此主题的更多信息，请参见知识库文章“Internet 上打包 MFC 控件的使用”\(Q167158\)。  知识库文章位于 MSDN Library CD\-ROM中或 [http:\/\/support.microsoft.com\/support\/](http://support.microsoft.com/support) 上。  
  
### CODEBASE 标记  
 使用 `<OBJECT>` 标记，ActiveX 控件嵌入在网页中。  `<OBJECT>` 标记的 `CODEBASE` 参数指定控件下载的位置。  `CODEBASE` 成功指出许多不同的文件类型。  
  
### OCX 文件中使用 CODEBASE 标记  
  
```  
CODEBASE="http://example.microsoft.com/mycontrol.ocx#version=4,70,0,1086"  
```  
  
 此解决方案只下载控件的 .ocx 文件，并要求客户端已经安装了所有支持的 DLL。  因为 Internet Explorer 随 Visual C\+\+ 控件的支持 DLL 过度，所以此将会在 Internet Explorer 和与 Visual C\+\+ 一起创建的 MFC ActiveX 控件中起作用。  如果另一个支持 ActiveX 控件的 Internet 浏览器用于查看此控件，此解决方案将不起作用。  
  
### INF 文件中使用 CODEBASE 标记  
  
```  
CODEBASE="http://example.microsoft.com/trustme.inf"  
```  
  
 .inf 文件将控制 .ocx 文件的安装及其支持的文件。  建议不要使用此方法，因为无法签名 .inf 文件 \(参见用于代码签名的指针 [代码签名](#_core_signing_code) \)。  
  
### CAB 文件中使用 CODEBASE 标记  
  
```  
CODEBASE="http://example.microsoft.com/acontrol.cab#version=1,2,0,0"  
```  
  
 Cabinet 文件是使用 MFC 打包 ActiveX 控件推荐的方法。  在 Cabinet 文件中打包 MFC ActiveX 控件允许 include .inf 文件来控制 ActiveX 控件和任何依赖的 DLL 的安装 \(如 MFC DLLs\)。  使用 CAB 文件自动压缩代码以便更快的下载。  如果将组件下载使用一 .cab 文件，它比每个组件是快速签名整个 .cab 文件。  
  
### 创建 CAB 文件  
 可以从知识库文章中的 [310618:Microsoft Cabinet Development Kit \(CDK\)](http://go.microsoft.com/fwlink/?LinkId=148204) 下载 Cabinet Development Kit。  在此工具箱中您将找到构造 cabinet 文件的必要的工具。  
  
 通过 `CODEBASE` 指向的 cabinet 文件应包含用于 ActiveX 控件的 .ocx 文件和 .inf 文件来控制其安装。  可以指定控制文件和 .inf 文件的名称来创建 Cabinet 文件。  不包括在本 Cabinet 文件的系统中可能已经存在的依赖 DLL。  例如，MFC DLLs 在单独的 Cabinet 文件打包并由控制 .inf 文件引用。  
  
 有关如何创建 CAB 文件的详细信息，请参见 [创建 CAB 文件](http://msdn.microsoft.com/zh-cn/cc52fd09-bdf6-4410-a693-149a308f36a3)。  
  
### INF 文件：  
 下面的示例，spindial.inf，列出了 MFC Spindial 控件需要的支持文件和版本信息。  注意到的 MFC DLLs 的位置是一个 Microsoft 站点。  Microsoft 提供并签名 mfc42.cab 。  
  
```  
Contents of spindial.inf:  
[mfc42installer]   
file-win32-x86=http://activex.microsoft.com/controls/vc/mfc42.cab   
[Olepro32.dll] - FileVersion=5,0,4261,0  
[Mfc42.dll] - FileVersion=6,0,8168,0  
[Msvcrt.dll] - FileVersion=6,0,8168,0  
```  
  
### \<OBJECT\> 标记  
 下面的示例演示如何使用 `<OBJECT>` 标记包装 MFC Spindial 示例控件。  
  
```  
<OBJECT ID="Spindial1" WIDTH=100 HEIGHT=51  
  CLASSID="CLSID:06889605-B8D0-101A-91F1-00608CEAD5B3"  
  CODEBASE="http://example.microsoft.com/spindial.cab#Version=1,0,0,001">  
    <PARAM NAME="_Version" VALUE="65536">  
    <PARAM NAME="_ExtentX" VALUE="2646">  
    <PARAM NAME="_ExtentY" VALUE="1323">  
    <PARAM NAME="_StockProps" VALUE="0">  
    <PARAM NAME="NeedlePosition" VALUE="2">  
</OBJECT>  
```  
  
 在这种情况下，spindial.cab 将包含两个文件，spindial.ocx 和 spindial.inf。  下面的命令将生成 Cabinet 文件：  
  
```  
C:\CabDevKit\cabarc.exe -s 6144 N spindial.cab spindial.ocx spindial.inf   
```  
  
 `–s 6144` 参数在 cabinet 中为代码签名保留空间。  
  
### 版本标记  
 请注意此时 `#Version` 信息由适用于 `<OBJECT>` 标记的 `CLASSID` 参数指定的控件 CAB 文件指定。  
  
 根据指定版本，可以强制下载控件。  有关包括 `OBJECT` 标记的 `CODEBASE` 参数的完整规范，请参见 W3C 引用。  
  
##  <a name="_core_marking_a_control_safe_for_scripting_and_initializing"></a> 标记脚本并初始化的一个安全控件  
 如果它们实际上安全，应将在网页中使用的 ActiveX 控件标记为脚本及初始化的安全可靠。  一个安全控件不会直接执行磁盘 IO 或访问您的计算机的内存或注册表。  
  
 通过注册表控件可以被标记作为脚本及初始化安全可靠。  修改 `DllRegisterServer` 添加实体类似于以下在注册表中将控件标记为脚本和持久性的安全。  一个替代方法是实现 `IObjectSafety`。  
  
 为控件定义 GUID \(全局唯一标识符\) 中将其标记为脚本和持久性安全。  可以安全脚本编写的控件将包含一注册表项与下面类似：  
  
```  
HKEY_CLASSES_ROOT\Component Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}  
```  
  
 可以从持久数据安全初始化的控件是使用注册表项标记为持久性安全类似于：  
  
```  
HKEY_CLASSES_ROOT\Component Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}  
```  
  
 添加输入类似以下 \(重写控件的类 ID 替换 `{06889605-B8D0-101A-91F1-00608CEAD5B3}`\) 使用以下类 ID 关联键:  
  
```  
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}   
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}   
```  
  
##  <a name="_core_licensing_issues"></a> 发行许可证  
 如果要在网页上使用一个授权控件，必须验证许可条款允许其在 Internet 上使用并为它创建一个许可证包文件 \(LPK\) 。  
  
 如果计算机运行的 Internet Explorer 没有使用此控件的许可，授权的 ActiveX 控件在 HTML 页不会被正确加载。  例如，如果已使用 Visual C\+\+ 生成授权控件，使用控件的 HTML 页在控件生成的计算机上将被正确加载，但对其他计算机不会加载，除非许可证信息包括在内。  
  
 若要使用已授权的 ActiveX 控件在 Internet Explorer，则必须检查提供程序的许可协议验证控件的许可证允许：  
  
-   Redistribution \(重新分发\)  
  
-   在 Internet 上使用控件  
  
-   Codebase 参数的使用  
  
 若要在没有授权的机器上使用将一个带有授权控件的 HTML 页，必须生成许可证包文件 \(LPK\)。  LPK 文件针对于 HTML 页中授权控件包含运行时许可证。  此文件通过 LPK\_TOOL.EXE 随 ActiveX SDK 的生成。  有关详细信息，请参见 Microsoft 网站： [http:\/\/msdn.microsoft.com](http://msdn.microsoft.com).  
  
#### 创建 LPK 文件  
  
1.  运行已允许控件使用的计算机上的 LPK\_TOOL.EXE。  
  
2.  在 **License Package Authoring Tool \(证件包授权工具\)** 对话框中，在 **Available （可用）控件** 列表框中，选择将要用于 HTML 页上每个授权的 ActiveX 控件并单击 **添加**。  
  
3.  单击 **Save \(保存\)& Exit （编辑）** 并为 LPK 文件键入一个名称。  这将创建 LPK 文件并结束应用程序。  
  
#### 在 HTML 页上嵌入一个授权控件  
  
1.  编辑 HTML 页。  在 HTML 页中，在其他任何 \<OBJECT\> 标记之前，为许可证管理器对象插入一 \<OBJECT\> 标记。  许可证管理器是与 Internet Explorer 一起安装的 ActiveX 控件。  其类 ID 如下所示。  将许可证管理器对象的 LPKPath 属性设置为 LPK 文件的路径和名称。  每个 HTML 页面只能具有一个 LPK 文件。  
  
    ```  
    <OBJECT CLASSID = "clsid:5220cb21-c88d-11cf-b347-00aa00a28331">  
        <PARAM NAME="LPKPath" VALUE="relative URL to .LPK file">  
    </OBJECT>  
    ```  
  
2.  在许可证管理器标记后面，为授权控件插入 \<OBJECT\> 标记，。  
  
     例如，显示 Microsoft 屏蔽编辑控件的 HTML 页如下所示。  第一个类 ID 是许可证管理器控件的，第二个类 ID 用于被屏蔽编辑控件。  更改标记指向您之前创建 .lpk 文件的相对路径，并添加对象标记包括控件类 ID 为您的控件。  
  
3.  为您的 LPK 文件插入 \<EMBED\> 特性，因此，如果使用 NCompass ActiveX 插件。  
  
     如果控件可能在其他活动启用的浏览器中显示，例如 Netscape 使用 NCompass ActiveX 插件 \- 必须添加 \<EMBED\> 语法如下所示。  
  
    ```  
    <OBJECT CLASSID="clsid:5220cb21-c88d-11cf-b347-00aa00a28331">  
        <PARAM NAME="LPKPath" VALUE="maskedit.lpk">  
  
        <EMBED SRC = "maskedit.LPK">  
  
    </OBJECT>  
    <OBJECT CLASSID="clsid:C932BA85-4374-101B-A56C-00AA003668DC" WIDTH=100 HEIGHT=25>  
    </OBJECT>  
    ```  
  
 有关控件授权的更多信息，请参见[ActiveX 控件：授权 ActiveX 控件](../mfc/mfc-activex-controls-licensing-an-activex-control.md)。  
  
##  <a name="_core_signing_code"></a> 签名代码  
 代码签名设计用于标识源代码以及保证代码在签名之后不能更改。  根据浏览器安全性设置，在代码下载之前，用户可能会被警告。  用户可能选择某些信任证书的所有者或公司，在这种情况下，这些信任的签名的下载代码将没有警告。  代码数字签名是为了避免被篡改。  
  
 确保最终代码被签名，以使控件可以自动下载，从而不显示信任的警告消息。  有关如何签名代码的详细信息，检查在 Authenticode 中的 ActiveX SDK 文档并参见 [签名 CAB 文件](http://msdn.microsoft.com/zh-cn/04d8b47a-8f1c-4b54-ab90-730fcdc03747)。  
  
 根据浏览器信任和安全级别设置，证书可能显示以确定签名的人员和公司。  如果安全级别是 None，或者，如果签名控件的证书所有者是受信任的，证书将不会被显示。  参见 [Internet Explorer 浏览器安全级别和控件行为](#_core_internet_explorer_browser_safety_levels_and_control_behavior) 查看有关如何设置浏览器安全级别来确定控件是否下载证书并显示的细节。  
  
 数字签名保证代码在签名之后未发生更改。  在证书中采用并嵌入了代码的哈希。  此哈希之后将会与代码下载后运行前的代码的哈希进行比较。  公司如 Verisign 可以提供代码签名必需的私有和公钥。  ActiveX SDK 附带 MakeCert，创建的测试证书一个实用工具。  
  
##  <a name="_core_managing_the_palette"></a> 管理调色板  
 容器确定调色板并使其可以作为一环境属性，**DISPID\_AMBIENT\_PALETTE**。  容器 \(例如，Internet Explorer\) 选择与页面上所有 ActiveX 控件使用的调色板来确定它们自己的调色板。  这防止闪烁的显示并提供一致的外观。  
  
 控件可以重写 `OnAmbientPropertyChange` 来处理更改调色板的通知。  
  
 控件可以重写 `OnGetColorSet` 来返回绘制调色板的颜色设置。  容器使用返回值决定控件是否支持调色板。  
  
 在 OCX 96 原则下，控件必须总是在后台实现其调色板。  
  
 不使用环境调色板属性的旧容器将发送的 `WM_QUERYNEWPALETTE` 和 `WM_PALETTECHANGED` 信息。  控件可以重写 `OnQueryNewPalette` 和 `OnPaletteChanged` 处理这些消息。  
  
##  <a name="_core_internet_explorer_browser_safety_levels_and_control_behavior"></a> Internet Explorer 浏览器安全级别和控件的行为  
 浏览器具有安全级别的选项，可由用户配置。  由于网页可以包含可能地危害用户计算机的活动内容，浏览器提供了允许用户选择安全级别的选项。  根据浏览器实现的安全性级别，控件可能不能被下载，或者会显示一个证书或警告信息来让用户选择在运行时是否下载此控件。  在 Internet Explorer 中高级，中等和低级的安全级别下 ActiveX 的控件行为在以下列出。  
  
### 高安全模式  
  
-   未签名的控件将不下载。  
  
-   签名控件如果不受信任将显示证书 \(用户可以选择从现在开始始终信任来自此证书所有者的代码\)。  
  
-   只有控件被标记为安全后将具有持久数据 和\/或可以在其上编写脚本。  
  
### 中等安全模式  
  
-   未签名控件在下载前将显示警告。  
  
-   签名控件如果不受信任，将显示证书。  
  
-   未标记为安全的控件将显示警告。  
  
### 低安全模式  
  
-   下载控件不显示警告。  
  
-   编写脚本和持久性上不出现警告。  
  
## 请参阅  
 [MFC Internet 编程任务](../mfc/mfc-internet-programming-tasks.md)   
 [MFC Internet 编程基础知识](../mfc/mfc-internet-programming-basics.md)   
 [MFC ActiveX 控件：许可 ActiveX 控件](../mfc/mfc-activex-controls-licensing-an-activex-control.md)