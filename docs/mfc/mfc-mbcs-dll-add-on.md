---
title: MFC MBCS DLL 加载项
ms.date: 05/08/2019
helpviewer_keywords:
- MBCS
- MFC
ms.openlocfilehash: 20145b200a0f8bac8ccb461331d4d233a3b0251e
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524822"
---
# <a name="mfc-mbcs-dll-add-on"></a>MFC MBCS DLL 加载项

对 MFC 的支持和其多字节字符集 (mbcs) 库在 Visual Studio 2013 及更高版本的 Visual Studio 安装过程中需要一个额外的步骤。

**Visual Studio 2013**:默认情况下，安装 Visual Studio 2013 中的 MFC 库仅支持 Unicode 开发。 需要 MBCS Dll 来生成具有 Visual Studio 2013 中的 MFC 项目**字符集**属性设置为**使用多字节字符集**或**未设置**。 下载在 DLL[适用于 Visual Studio 2013 的多字节 MFC 库](https://www.microsoft.com/download/details.aspx?id=40770)。

**Visual Studio 2015**：Unicode 和 MBCS MFC Dll 包含在视觉对象C++的安装组件，但默认情况下不安装 MFC 对的支持。 在 Visual Studio 安装程序中，Visual C++ 和 MFC 是可选安装配置。 若要确保已安装 MFC，请在安装程序中选择“自定义”  ，并确保在“编程语言” 下选择了“Visual C++”  和“用于 C++ 的 Microsoft 基础类”  。 如果已安装 Visual Studio，则尝试创建 MFC 项目时，系统将提示你安装 Visual C++ 和/或 MFC。

**Visual Studio 2017 及更高版本**：与安装了 Unicode 和 MBCS MFC Dll**使用的桌面开发C++** 当你选择的工作负荷**MFC 和 ATL 支持**从**可选组件**窗格。 如果您的安装不包括这些组件，导航到**文件 |新项目**对话框，然后单击**打开 Visual Studio 安装程序**链接。

## <a name="see-also"></a>请参阅

[MFC 库版本](../mfc/mfc-library-versions.md)
