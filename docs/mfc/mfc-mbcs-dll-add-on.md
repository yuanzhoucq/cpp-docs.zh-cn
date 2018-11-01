---
title: MFC MBCS DLL 加载项
ms.date: 1/04/2018
helpviewer_keywords:
- MBCS
- MFC
ms.openlocfilehash: a78425ac92aa9ddfe7f0b1b61dde915b3e088383
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558907"
---
# <a name="mfc-mbcs-dll-add-on"></a>MFC MBCS DLL 加载项

对 MFC 的支持和其多字节字符集 (mbcs) 库 2015年和 2017年的 Visual Studio 2013 中的 Visual Studio 安装期间需要一个额外的步骤。

**Visual Studio 2013**： 默认情况下，安装 Visual Studio 2013 中的 MFC 库仅支持 Unicode 开发。 需要 MBCS Dll 来生成具有 Visual Studio 2013 中的 MFC 项目**字符集**属性设置为**使用多字节字符集**或**未设置**。 下载在 DLL[适用于 Visual Studio 2013 的多字节 MFC 库](https://www.microsoft.com/download/details.aspx?id=40770)。

**Visual Studio 2015**： 两个 Unicode 和 MBCS MFC Dll 包含在 Visual c + + 安装组件，但默认情况下不安装 MFC 对的支持。 在 Visual Studio 安装程序中，Visual C++ 和 MFC 是可选安装配置。 若要确保已安装 MFC，请在安装程序中选择“自定义”  ，并确保在“编程语言” 下选择了“Visual C++”  和“用于 C++ 的 Microsoft 基础类”  。 如果已安装 Visual Studio，则尝试创建 MFC 项目时，系统将提示你安装 Visual C++ 和/或 MFC。

**Visual Studio 2017**： 使用安装的 Unicode 和 MBCS MFC Dll**使用 c + + 的桌面开发**时选择的工作负荷**MFC 和 ATL 支持**从**可选组件**窗格。 如果您的安装不包括这些组件，导航到**文件 |新项目**对话框，然后单击**打开 Visual Studio 安装程序**链接。

## <a name="see-also"></a>请参阅

[MFC 库版本](../mfc/mfc-library-versions.md)

