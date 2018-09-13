---
title: 升级现有 ActiveX 控件 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [MFC], Internet
- LPK files for Internet controls
- safe for scripting and initialization (controls)
- OLE controls [MFC], upgrading to ActiveX
- CAB files, for ActiveX controls
- Internet applications [MFC], ActiveX controls
- Internet applications [MFC], packaging code for download
- upgrading ActiveX controls
- licensing ActiveX controls
ms.assetid: 4d12ddfa-b491-4f9f-a0b7-b51458e05651
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0bca0cca66f7f8b9c59dcea4911550abfc2024c8
ms.sourcegitcommit: b4432d30f255f0cb58dce69cbc8cbcb9d44bc68b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/13/2018
ms.locfileid: "45535261"
---
# <a name="upgrading-an-existing-activex-control"></a>升级现有 ActiveX 控件
现有 ActiveX 控件（以前称为 OLE 控件）无需修改即可在 Internet 上使用。 但是，您可能希望修改控件以提高其性能。 

>[!IMPORTANT]
> ActiveX 是一项传统技术，不应使用新的开发。 本文将取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](activex-controls.md)。

在网页上使用控件时，还有其他一些考虑因素。 .ocx 文件和所有支持文件必须在目标计算机上或者必须通过 Internet 下载。 这使代码大小和下载时间成为了一个重要考虑因素。 下载内容可在已签名的 .cab 文件中打包。 您可以将控件标记为对于脚本化或初始化是安全的。  
  
 本文讨论以下主题：  
  
- [用于下载的打包代码](#_core_packaging_code_for_downloading)  
  
- [将控件安全标记的脚本编写和初始化](#_core_marking_a_control_safe_for_scripting_and_initializing)  
  
- [许可问题](#_core_licensing_issues)  
  
- [代码签名](#_core_signing_code)  
  
- [管理调色板](#_core_managing_the_palette)  
  
- [Internet Explorer 浏览器安全级别和控件行为](#_core_internet_explorer_browser_safety_levels_and_control_behavior)  
  
 此外可以添加优化，如中所述[ActiveX 控件： 优化](../mfc/mfc-activex-controls-optimization.md)。 名字对象可用于下载属性和大型 Blob 以异步方式，如中所述[Internet 上的 ActiveX 控件](../mfc/activex-controls-on-the-internet.md)。  
  
##  <a name="_core_packaging_code_for_downloading"></a> 用于下载的打包代码  
 有关此主题的详细信息，请参阅知识库文章“打包 MFC 控件以便通过 Internet 使用”(Q167158)。 您可以找到知识库文章[ http://support.microsoft.com/support ](http://support.microsoft.com/support)。  
  
### <a name="the-codebase-tag"></a>CODEBASE 标记  
 ActiveX 控件是使用 `<OBJECT>` 标记嵌入在网页中的。 `CODEBASE` 标记的 `<OBJECT>` 参数指定从中下载控件的位置。 `CODEBASE` 可成功指向很多不同的文件类型。  
  
### <a name="using-the-codebase-tag-with-an-ocx-file"></a>将 CODEBASE 标记用于 OCX 文件  
  
```  
CODEBASE="http://example.microsoft.com/mycontrol.ocx#version=4,
    70,
    0,
    1086"  
```  
  
 此解决方案只下载控件的 .ocx 文件，并要求所有支持 DLL 已安装在客户端计算机上。 这适用于 Internet Explorer 和使用 Visual C++ 构建的 MFC ActiveX 控件，因为 Internet Explorer 附带有 Visual C++ 控件的支持 DLL。 如果使用了另一个支持 ActiveX 控件的 Internet 浏览器来查看此控件，此解决方案将不起作用。  
  
### <a name="using-the-codebase-tag-with-an-inf-file"></a>将 CODEBASE 标记用于 INF 文件  
  
```  
CODEBASE="http://example.microsoft.com/trustme.inf"  
```  
  
 .inf 文件将控制 .ocx 文件及其支持文件的安装。 不推荐使用此方法，因为它不可能.inf 文件进行签名 (请参阅[对代码进行签名](#_core_signing_code)有关代码签名的指针)。  
  
### <a name="using-the-codebase-tag-with-a-cab-file"></a>将 CODEBASE 标记用于 CAB 文件  
  
```  
CODEBASE="http://example.microsoft.com/acontrol.cab#version=1,
    2,
    0,
    0"  
```  
  
 Cabinet 文件是使用 MFC 打包 ActiveX 控件的推荐方法。 通过在 Cabinet 文件中打包 MFC ActiveX 控件，可以包含 .inf 文件来控制 ActiveX 控件和任何依赖 DLL（如 MFC DLL）的安装。 使用 CAB 文件可自动压缩代码以加快下载速度。 如果要使用 .cab 文件进行组件下载，对整个 .cab 文件进行签名比分别对每个组件进行签名速度更快。  
  
### <a name="creating-cab-files"></a>创建 CAB 文件  
 您可以从知识库文章中下载 Cabinet 开发工具包[310618: Microsoft Cabinet 开发工具包](http://go.microsoft.com/fwlink/p/?linkid=148204)。 在此工具包中，您将找到构造 Cabinet 文件所需的工具。  
  
 `CODEBASE` 指向的 Cabinet 文件应包含 ActiveX 控件的 .ocx 文件和用于控制其安装的 .inf 文件。 您可以通过指定控件文件的名称和一个 .inf 文件来创建 Cabinet 文件。 不要在此 Cabinet 文件中包含可能已存在于系统上的依赖 DLL。 例如，MFC DLL 在单独的 Cabinet 文件中打包并通过控制 .inf 文件来引用。  
  
 有关如何创建 CAB 文件的详细信息，请参阅[创建 CAB 文件](/windows/desktop/devnotes/cabinet-api-functions)。  
  
### <a name="the-inf-file"></a>INF 文件  
 以下示例 spindial.inf 列出了 MFC Spindial 控件所需的支持文件和版本信息。 请注意，MFC DLL 的位置是 Microsoft 网站。 mfc42.cab 由 Microsoft 提供和签名。  
  
```  
Contents of spindial.inf:  
[mfc42installer]   
file-win32-x86=http://activex.microsoft.com/controls/vc/mfc42.cab   
[Olepro32.dll] - FileVersion=5,
    0,
    4261,
    0  
[Mfc42.dll] - FileVersion=6,
    0,
    8168,
    0  
[Msvcrt.dll] - FileVersion=6,
    0,
    8168,
    0  
```  
  
### <a name="the-object-tag"></a>\<对象 > 标记  
 以下示例演示如何使用 `<OBJECT>` 标记打包 MFC Spindial 示例控件。  
  
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
  
 在这种情况下，spindial.cab 将包含两个文件：spindial.ocx 和 spindial.inf。 以下命令将生成 Cabinet 文件：  
  
```  
C:\CabDevKit\cabarc.exe -s 6144 N spindial.cab spindial.ocx spindial.inf   
```  
  
 `-s 6144`参数保留代码签名的 cab 文件中的空间。  
  
### <a name="the-version-tag"></a>版本标记  
 此处请注意，`#Version`指定使用 CAB 文件的信息适用于指定的控件*CLASSID*参数的`<OBJECT>`标记。  
  
 根据指定的版本，您可以强制下载控件。 有关的完整规范`OBJECT`标记包括*CODEBASE*参数，请参阅 W3C 参考。  
  
##  <a name="_core_marking_a_control_safe_for_scripting_and_initializing"></a> 将控件安全标记的脚本编写和初始化  
 如果网页中使用的 ActiveX 控件实际上是安全的，则应将它们标记为对于脚本化和初始化是安全的。 安全的控件不会直接执行磁盘 IO 或者访问计算机的内存或注册表。  
  
 可通过注册表将控件标记对于脚本和初始化是安全的。 修改 `DllRegisterServer` 可添加与下面类似的项，从而将控件标记为对于脚本化和注册表中的持久化是安全的。 一个替代方法是实现 `IObjectSafety`。  
  
 您将为控件定义 GUID（全局唯一标识符）将其标记为对于脚本化和持久性是安全的。 可以安全地脚本化的控件将包含与下面类似的注册表项：  
  
```  
HKEY_CLASSES_ROOT\Component Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}  
```  
  
 可以从持久性数据安全地初始化的控件被标记为对于与类似于下面的注册表项的持久性是安全的：  
  
```  
HKEY_CLASSES_ROOT\Component Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}  
```  
  
 添加与以下类似项 (替换控件的类来代替 ID `{06889605-B8D0-101A-91F1-00608CEAD5B3}`) 若要将你的密钥与以下类 ID 相关联：  
  
```  
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}   
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}   
```  
  
##  <a name="_core_licensing_issues"></a> 许可问题  
 如果要在网页上使用授权控件，则必须确认许可协议允许在 Internet 上使用该控件，并为它创建一个许可协议包文件 (LPK)。  
  
 如果运行 Internet Explorer 的计算机没有获得使用此控件的授权，授权 ActiveX 控件在 HTML 页中无法正确加载。 例如，如果使用 Visual C++ 生成了一个授权控件，使用该控件的 HTML 页将在生成该控件的计算机上正确加载，但 HTML 页在其他计算机上不会加载，除非已包含授权信息。  
  
 若要在 Internet Explorer 中使用授权 ActiveX 控件，则必须检查供应商的许可协议以验证许可证中的控件权限：  
  
-   重新分发  
  
-   控件在 Internet 上的使用  
  
-   Codebase 参数的使用  
  
 若要在未授权的计算机上在 HTML 页中使用授权控件，则必须生成许可协议包文件 (LPK)。 LPK 文件将授权控件的运行时许可证包含在 HTML 页中。 此文件通过 ActiveX SDK 附带的 LPK_TOOL.EXE 的生成。 有关详细信息，请参阅 MSDN 网站上的[ http://msdn.microsoft.com ](http://msdn.microsoft.com)。  
  
#### <a name="to-create-an-lpk-file"></a>若要创建 LPK 文件  
  
1.  在获得使用控件的授权的计算机上运行 LPK_TOOL.EXE。  
  
2.  在中**许可协议包创作工具**对话框中**可用控件**列表框中，选择每个授权 ActiveX 控件，将使用 HTML 页上，单击**添加**.  
  
3.  单击**保存并退出**并为 LPK 文件键入一个名称。 这将创建 LPK 文件并关闭应用程序。  
  
#### <a name="to-embed-a-licensed-control-on-an-html-page"></a>在 HTML 页上嵌入授权控件  
  
1.  编辑 HTML 页。 在 HTML 页中，插入\<对象 > 标记前任何其他许可证管理器对象\<对象 > 标记。 许可证管理器是与 Internet Explorer 一起安装的 ActiveX 控件。 其类 ID 如下所示。 将许可证管理器对象的 LPKPath 属性设置为 LPK 文件的路径和名称。 每个 HTML 页面只能有一个 LPK 文件。  
  
 ```  
 <OBJECT CLASSID = "clsid:5220cb21-c88d-11cf-b347-00aa00a28331">  
 <PARAM NAME="LPKPath" VALUE="relative URL to .LPK file">  
 </OBJECT>  
 ```  
  
2.  插入\<对象 > 标记为授权控件许可证管理器标记之后。  
  
     例如，显示 Microsoft Masked Edit 控件的 HTML 页如下所示。 第一个类 ID 用于许可证管理器控件，第二个类 ID 用于 Masked Edit 控件。 将标记更改为指向之前创建的 .lpk 文件的相对路径，并添加对象标记（包括控件的类 ID）。  
  
3.  插入\<嵌入 > 属性为 LPK 文件，如果使用 NCompass ActiveX 插件。  
  
     如果您的控件可能会查看其他活动启用浏览器-例如，使用 NCompass ActiveX 插件的 Netscape — 您必须添加\<嵌入 > 语法如下所示。  
  
 ```  
 <OBJECT CLASSID="clsid:5220cb21-c88d-11cf-b347-00aa00a28331">  
 <PARAM NAME="LPKPath" VALUE="maskedit.lpk">  
 
 <EMBED SRC = "maskedit.LPK">  
 
 </OBJECT>  
 <OBJECT CLASSID="clsid:C932BA85-4374-101B-A56C-00AA003668DC" WIDTH=100 HEIGHT=25>  
 </OBJECT>  
 ```  
  
 有关控件授权详细信息，请参阅[ActiveX 控件： 许可 ActiveX 控件](../mfc/mfc-activex-controls-licensing-an-activex-control.md)。  
  
##  <a name="_core_signing_code"></a> 代码签名  
 代码签名专用于标识代码的源和保证代码在签名后未发生更改。 在下载代码之前，用户可能会收到警告，具体取决于浏览器安全设置。 用户可能选择信任某些证书所有者或公司，在这种情况下，这些受信任方签名的代码可以直接下载，不会发出警告。 将对代码进行数字签名以避免篡改。  
  
 请确保对最终代码进行了签名，以便让控件可以自动下载而不显示信任警告消息。 了解代码进行签名的详细信息，请查看 ActiveX SDK 中的 Authenticode 上文档并查看[签名 CAB 文件](/windows/desktop/devnotes/cabinet-api-functions)。  
  
 可能显示证书来标识签名人员和公司，具体取决于信任和浏览器安全级别设置。 如果安全级别是“无”，或者已签名的控件的证书所有者是受信任的，证书将不会显示。 请参阅[Internet Explorer 浏览器安全级别和控件行为](#_core_internet_explorer_browser_safety_levels_and_control_behavior)有关如何浏览器安全设置将确定是否下载控件和显示证书的详细信息。  
  
 数字签名可保证代码在签名后未发生更改。 在证书中采用并嵌入了代码哈希。 此哈希随后会与代码下载后但尚未运行前采用的代码哈希进行比较。 公司（如 Verisign）可提供对代码进行签名所需的私钥和公钥。 ActiveX SDK 附带了 MakeCert - 创建测试证书的实用工具。  
  
##  <a name="_core_managing_the_palette"></a> 管理调色板  
 容器将确定调色板并使其可作为环境属性， **DISPID_AMBIENT_PALETTE**。 容器（例如，Internet Explorer）选择页面上的所有 ActiveX 控件使用的调色板来确定其自己的调色板。 这将防止显示闪烁并提供一致的外观。  
  
 控件可重写 `OnAmbientPropertyChange` 来处理调色板发生更改的通知。  
  
 控件可重写 `OnGetColorSet` 来返回绘制调色板的颜色集。 容器使用返回值确定控件是否支持调色板。  
  
 在 OCX 96 准则下，控件必须总是在后台实现其调色板。  
  
 不使用环境调色板属性的旧容器将发送 WM_QUERYNEWPALETTE 和 WM_PALETTECHANGED 消息。 控件可重写 `OnQueryNewPalette` 和 `OnPaletteChanged` 来处理这些消息。  
  
##  <a name="_core_internet_explorer_browser_safety_levels_and_control_behavior"></a> Internet Explorer 浏览器安全级别和控件行为  
 浏览器具有可由用户配置的安全级别的选项。 由于网页可能包含对用户的计算机具有潜在威胁的活动内容，浏览器允许用户选择安全级别的选项。 控件可能完全不能下载，或者会显示证书或警告消息来允许用户在运行时选择是否下载控件，具体取决于浏览器实现安全级别的方式。 下面列出了在 Internet Explorer 中上处于高、中和低安全级别的 ActiveX 控件的行为。  
  
### <a name="high-safety-mode"></a>高安全级模式  
  
-   不下载未签名的控件。  
  
-   已签名的控件在不受信任时将显示证书（用户可以选择从现在起始终信任来自此证书所有者的代码的选项）。  
  
-   只有标记为安全的控件具有持久性数据和/或可脚本化。  
  
### <a name="medium-safety-mode"></a>中等安全模式  
  
-   未签名的控件将在下载前显示警告。  
  
-   已签名的控件在不受信任时将显示证书。  
  
-   未标记为安全的控件将显示警告。  
  
### <a name="low-safety-mode"></a>低安全级模式  
  
-   下载控件时不出现警告。  
  
-   发生脚本化和持久性时不出现警告。  
  
## <a name="see-also"></a>请参阅  
 [MFC Internet 编程任务](../mfc/mfc-internet-programming-tasks.md)   
 [MFC Internet 编程基础知识](../mfc/mfc-internet-programming-basics.md)   
 [MFC ActiveX 控件：许可 ActiveX 控件](../mfc/mfc-activex-controls-licensing-an-activex-control.md)

