---
title: 帮助文件 (WinHelp)
ms.date: 11/04/2016
helpviewer_keywords:
- file types [C++], WinHelp files
ms.assetid: 4fdcbd66-66b0-4866-894a-fd7b4c2557e4
ms.openlocfilehash: 142702699523633bf810d0077ce7ba6355557d21
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496285"
---
# <a name="help-files-winhelp"></a>帮助文件 (WinHelp)

在 MFC 应用程序向导的[高级功能](../mfc/reference/advanced-features-mfc-application-wizard.md)页中，选中“上下文相关帮助”复选框，然后选择“WinHelp 格式”，将 WinHelp 类型的帮助支持添加到应用程序时，将创建以下文件。

|文件名|目录位置|解决方案资源管理器位置|描述|
|---------------|------------------------|--------------------------------|-----------------|
|Projname.hpj|Projname\hlp|源文件|帮助编译器创建程序或控件的帮助文件时使用的帮助项目文件。|
|Projname.rtf|Projname\hlp|帮助文件|包含可编辑的模板主题以及有关自定义 .hpj 文件的信息。|
|Projname.cnt|Projname\hlp|帮助文件|为 Windows 帮助中的“内容”窗口提供结构。|
|Makehelp.bat|Projname|源文件|编译项目时，系统使用它来生成帮助项目。|
|Print.rtf|Projname\hlp|帮助文件|如果项目包括打印支持（默认设置），则进行创建。 描述打印命令和对话框。|
|*.bmp|Projname\hlp|资源文件|包含所生成的不同帮助文件主题的图像。|

通过在 MFC ActiveX 控件向导的[应用程序设置](../mfc/reference/application-settings-mfc-activex-control-wizard.md)选项卡中选择“生成帮助文件”，可将 WinHelp 支持添加到 MFC ActiveX 控件项目。 将帮助支持添加到 MFC ActiveX 控件时，以下文件将添加到项目中：

|文件名|目录位置|解决方案资源管理器位置|描述|
|---------------|------------------------|--------------------------------|-----------------|
|Projname.hpj|Projname\hlp|源文件|帮助编译器创建程序或控件的帮助文件时使用的项目文件。|
|Projname.rtf|Projname\hlp|项目|包含可编辑的模板主题以及有关自定义 .hpj 文件的信息。|
|Makehelp.bat|Projname|源文件|编译项目时，系统使用它来生成帮助项目。|
|Bullet.bmp|Projname|资源文件|标准帮助文件主题使用它来表示项目符号列表。|

## <a name="see-also"></a>请参阅

[为 Visual C++ 项目创建的文件类型](../ide/file-types-created-for-visual-cpp-projects.md)