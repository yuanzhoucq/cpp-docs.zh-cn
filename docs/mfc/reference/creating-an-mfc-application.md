---
title: 创建 MFC 应用程序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- applications [MFC]
- MFC, creating applications
- MFC applications
ms.assetid: b8b8aa08-9c49-404c-8078-b42079ac18f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c20d3214f8f2f76fedaeebcd439f10e016ccdd9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410632"
---
# <a name="creating-an-mfc-application"></a>创建 MFC 应用程序

MFC 应用程序是基于 Microsoft 基础类 (MFC) 库的 Windows 可执行应用程序。 创建 MFC 应用程序的最容易方法是使用 MFC 应用程序向导。

> [!IMPORTANT]
>  Visual Studio Express 版本不支持 MFC 项目。

MFC 可执行文件通常分为五类： 标准 Windows 应用程序、 对话框、 基于窗体的应用程序、 资源管理器样式的应用程序和 Web 浏览器样式的应用程序。 有关详细信息，请参见:

- [使用类编写 Windows 应用程序](../../mfc/using-the-classes-to-write-applications-for-windows.md)

- [创建并显示对话框](../../mfc/creating-and-displaying-dialog-boxes.md)

- [创建基于窗体的 MFC 应用程序](../../mfc/reference/creating-a-forms-based-mfc-application.md)

- [创建文件资源管理器样式的 MFC 应用程序](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)

- [创建 Web 浏览器样式的 MFC 应用程序](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)

根据在向导中选择的选项，MFC 应用程序向导为上述任何应用程序生成适当的类和文件。

### <a name="to-create-an-mfc-application-using-the-mfc-application-wizard"></a>使用 MFC 应用程序向导创建 MFC 应用程序

1. 请按帮助主题[使用 Visual C++ 应用程序向导创建项目](../../ide/creating-desktop-projects-by-using-application-wizards.md)中的说明进行操作。

1. 在中**新的项目**对话框中，选择**MFC 应用程序**在模板窗格中，以打开向导。

1. 定义使用应用程序设置[MFC 应用程序向导](../../mfc/reference/mfc-application-wizard.md)。

    > [!NOTE]
    >  跳过此步骤可保留向导的默认设置。

1. 单击**完成**关闭向导并在开发环境中打开新项目。

你的项目创建后，可以查看中创建的文件**解决方案资源管理器**。 有关向导为项目创建的文件的更多信息，请参见项目生成的文件 ReadMe.txt。 有关文件类型的详细信息，请参阅[Visual c + + 项目创建的文件类型](../../ide/file-types-created-for-visual-cpp-projects.md)。

## <a name="see-also"></a>请参阅

[用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[属性页](../../ide/property-pages-visual-cpp.md)


