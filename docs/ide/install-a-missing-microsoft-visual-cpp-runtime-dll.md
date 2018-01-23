---
title: "安装缺少 Microsoft Visual c + + 运行时 DLL |Microsoft 文档"
description: "如何查找和安装缺少 Visual c + + 运行时 Dll。"
ms.date: 08/30/2017
ms.topic: article
ms.prod: visual-cpp
dev_langs: C++
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b9037a50740c55d7dd997fd86744459b6fb96125
ms.sourcegitcommit: 6f40bba1772a09ff0e3843d5f70b553e1a15ab50
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/22/2018
---
# <a name="install-a-missing-microsoft-visual-c-runtime-dll"></a>安装缺少 Microsoft Visual c + + 运行时 DLL

通常使用 Microsoft Visual c + + 编写的程序需要某些其他 Visual c + + 运行时库文件，文件或 Dll，来运行。 这些运行时 Dll 均可用在*可再发行组件包*，库文件安装程序，每个版本的 Visual c + +。 所需的任何程序的可再发行组件包应包含由其安装程序。 如果不是，有时可以自行安装可再发行组件包和运行程序时，修复系统错误。 

你可以判断是否在开始类似以下内容的程序时收到系统错误，缺少程序 Visual c + + 运行时 DLL 像"VCRuntime140.dll 是你的计算机缺少，无法启动的程序"。 通常情况下，可以通过卸载程序，然后重新安装修复此问题。 我们强烈建议首先，尝试此步骤之前任何其他潜在修复。

有时可再发行组件包安装程序已过期。 Microsoft 可更新的运行时 Dll 版本有时，向地址 bug 和安全问题。 若要使运行安全地和正确的计算机，它是针对任何运行时 DLL 中使用的最新的更新一个好办法。 检查以查看是否存在可用于您的程序，可能会为你提供此更新的更新的安装程序。 如果没有，然后使用更新的安装程序重新安装程序。

如果重新安装程序不会进行消失的系统错误，然后程序安装程序可能损坏，或者已损坏，或在你的计算机上运行时 Dll 可能已损坏。 尝试下载的安装程序，程序的新副本，并使用它来重新安装第一个。 如果这不起作用，或者安装程序不可用，则可能值得检查您的计算机上的 Microsoft Visual c + + 可再发行组件安装它。 

下表显示的一个或多个可再发行组件包，以及链接以下载可再发行组件包的副本中包括 Dll 的列表。 下载可再发行组件包的新副本之前，你应看到是否则可以修复现有安装。

|缺少 DLL  |可再发行组件包  |
|---------|---------|
|atl80.dll<br />msvcm80.dll<br />msvcp80.dll<br />msvcr80.dll<br />mfc80.dll<br />mfc80u.dll<br />mfcm80.dll<br />mfcm80u.dll|[Microsoft Visual c + + 2005 可再发行组件 (x86)](https://www.microsoft.com/en-us/download/details.aspx?id=5638)<br />[Microsoft Visual c + + 2005年可再发行组件包 (x64)](https://www.microsoft.com/en-us/download/details.aspx?id=18471)<br />[Microsoft Visual c + + 2005 Service Pack 1 可再发行组件包 MFC 安全更新](https://www.microsoft.com/en-us/download/details.aspx?id=26347)|
|atl90.dll<br />msvcr90.dll<br />msvcm90.dll<br />msvcp90.dll<br />mfc90.dll<br />mfc90u.dll<br />mfcmifc80.dll<br />mfcm90.dll<br />mfcm90u.dll|[Microsoft Visual c + + 2008 可再发行组件的 x86](https://www.microsoft.com/en-us/download/details.aspx?id=5582)<br />[Microsoft Visual c + + 2008 可再发行组件的 x64](https://www.microsoft.com/en-us/download/details.aspx?id=2092)<br />[Microsoft Visual c + + 2008 Service Pack 1 可再发行组件包 MFC 安全更新](https://www.microsoft.com/en-us/download/details.aspx?id=26368)|
|atl100.dll<br />msvcr100.dll<br />msvcp100.dll<br />msdia71.dll<br />vcomp100.dll<br />mfc100.dll<br />mfc100u.dll<br />mfcmifc80.dll<br />mfcm100.dll<br />mfcm100u.dll|[Microsoft Visual c + + 2010 x86 可再发行组件](https://www.microsoft.com/en-us/download/details.aspx?id=8328)<br />[Microsoft Visual c + + 2010 x64 可再发行组件](https://www.microsoft.com/en-us/download/details.aspx?id=13523)<br />[Microsoft Visual c + + 2010 Service Pack 1 可再发行组件包 MFC 安全更新](https://www.microsoft.com/en-us/download/details.aspx?id=26999)|
|atl110.dll<br />msvcr110.dll<br />msvcp110.dll<br />mfc110.dll<br />mfc110u.dll<br />mfcmifc80.dll<br />mfcm110.dll<br />mfcm110u.dll<br />concrt110.dll<br />vccorlib110.dll<br />vcamp110.dll<br />vcomp110.dll|[Microsoft Visual c + + 2012 可再发行组件 （适用于 Visual Studio 2012 Update 4)](https://www.microsoft.com/en-us/download/details.aspx?id=30679)|
|msvcr120.dll<br />msvcp120.dll<br />mfc120.dll<br />mfc120u.dll<br />mfcmifc80.dll<br />mfcm120.dll<br />mfcm120u.dll<br />concrt120.dll<br />vccorlib120.dll<br />vcamp120.dll<br />vcomp120.dll|[Microsoft Visual c + + 2013年可再发行组件 （单独的下载链接）](https://support.microsoft.com/en-us/help/3179560/update-for-visual-c-2013-and-visual-c-redistributable-package)<br />[Visual Studio 2013 的多字节的 MFC 库](https://www.microsoft.com/en-us/download/details.aspx?id=40770)<br />[旁加载 Windows 8.1 应用 （.zip 下载） 的 visual c + + 2013年运行时](http://download.microsoft.com/download/5/F/0/5F0F8404-9329-44A9-8176-ED6F7F746F25/VCLibs_Redist_Packages.zip)|
|vcruntime140.dll<br />vcruntime140_app.dll<br />msvcp140.dll<br />mfc140.dll<br />mfc140u.dll<br />mfcmifc80.dll<br />mfcm140.dll<br />mfcm140u.dll<br />concrt140.dll<br />vccorlib140.dll<br />vcamp140.dll<br />vcomp140.dll|[Microsoft Visual c + + 自 2017 年 1 可再发行组件 (x86)](https://go.microsoft.com/fwlink/?LinkId=746571)<br />[Microsoft Visual c + + 自 2017 年 1 可再发行组件 (x64)](https://go.microsoft.com/fwlink/?LinkId=746572)|
|msvcr100_clr0400.dll<br />msvcr110_clr0400.dll<br />msvcr120_clr0400.dll|[下载 .NET Framework](https://www.microsoft.com/net/download/framework)|

### <a name="to-repair-an-existing-redistributable-package"></a>若要修复的现有的可再发行组件包

1. 打开控制面板。 在 Windows 10 中，输入*控制面板*桌面中在任务栏中，搜索控件，然后选择**控制面板**从提供的选项。

2. 在控制面板中，选择**程序** > **程序和功能**。 选择 Microsoft Visual c + + 可再发行的对应于缺少的 DLL 版本。 如果**更改**按钮将显示在顶部列表中，选择它。 如果唯一的选择是**卸载**，不能修复此版本的可再发行组件包。

3. 选择**修复**安装程序对话框中的可再发行组件包。 你可能需要重新启动完成修复时。 