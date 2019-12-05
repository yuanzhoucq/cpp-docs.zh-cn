---
title: MFC MBCS DLL 加载项
ms.date: 12/02/2019
helpviewer_keywords:
- MBCS
- MFC
ms.openlocfilehash: fe74e0639664b6a6a86a4c3269f174de441002f4
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810369"
---
# <a name="mfc-mbcs-dll-add-on"></a>MFC MBCS DLL 加载项

在 Visual Studio 2013 和更高版本的 Visual Studio 安装过程中，支持 MFC 及其多字节字符集（MBCS）库需要额外的步骤。

**Visual Studio 2013**：默认情况下，安装在 Visual Studio 2013 中的 MFC 库仅支持 Unicode 开发。 需要使用 MBCS Dll 才能在将**字符集**属性设置为 "**使用多字节字符集**" 或 "**未设置**" 的 Visual Studio 2013 中生成 MFC 项目。 下载[Visual Studio 2013 的多字节 MFC 库](https://www.microsoft.com/download/details.aspx?id=40770)中的 DLL。

**Visual Studio 2015**： UNICODE 和 MBCS MFC dll 都包含在视觉对象C++安装组件中，但默认情况下不会安装对 mfc 的支持。 在 Visual Studio 安装程序中，Visual C++ 和 MFC 是可选安装配置。 若要确保已安装 MFC，请在安装程序中选择“自定义” ，并确保在“编程语言”下选择了“Visual C++” 和“用于 C++ 的 Microsoft 基础类” 。 如果已安装 Visual Studio，则尝试创建 MFC 项目时，系统将提示你安装 Visual C++ 和/或 MFC。

**Visual Studio 2017 及更高版本**：在 Visual Studio 安装程序程序的 "**可选组件**" 窗格中选择**MFC 和 ATL 支持**时，将随**桌面开发C++** 和工作负载一起安装 Unicode 和 MBCS mfc dll。 如果安装不包括这些组件，请导航到**文件 |"新建项目**" 对话框，然后单击 "**打开 Visual Studio 安装程序**" 链接。 有关详细信息，请参阅[安装 Visual Studio](/visualstudio/install/install-visual-studio)。

## <a name="see-also"></a>另请参阅

[MFC 库版本](../mfc/mfc-library-versions.md)
