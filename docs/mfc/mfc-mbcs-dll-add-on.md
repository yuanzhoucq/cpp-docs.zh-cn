---
title: "MFC MBCS DLL 加载项 |Microsoft 文档"
ms.custom: 
ms.date: 1/04/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MBCS
- MFC
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d6f134110ff95956cc37d6e038a680ff27cbc298
ms.sourcegitcommit: 56f6fce7d80e4f61d45752f4c8512e4ef0453e58
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/12/2018
---
# <a name="mfc-mbcs-dll-add-on"></a>MFC MBCS DLL 加载项

对 MFC 的支持和其多字节字符组 (MBCS) 库，在 Visual Studio 2013，2015 和自 2017 年中的 Visual Studio 安装期间需要附加步骤。

**Visual Studio 2013**： 默认情况下，安装 Visual Studio 2013 中的 MFC 库仅支持 Unicode 开发。 若要生成的具有 Visual Studio 2013 中的一个 MFC 项目需要 MBCS Dll**字符集**属性设置为**使用多字节字符集**或**未设置**。 下载在 DLL [Visual Studio 2013 的多字节的 MFC 库](https://www.microsoft.com/en-us/download/details.aspx?id=40770)。

**Visual Studio 2015**： 两个 Unicode 和 MBCS MFC Dll 包含在 Visual c + + 安装组件，但默认情况下不安装 MFC 对的支持。 在 Visual Studio 安装程序中，Visual C++ 和 MFC 是可选安装配置。 若要确保已安装 MFC，请在安装程序中选择“自定义”  ，并确保在“编程语言” 下选择了“Visual C++”  和“用于 C++ 的 Microsoft 基础类”  。 如果已安装 Visual Studio，则尝试创建 MFC 项目时，系统将提示你安装 Visual C++ 和/或 MFC。

**Visual Studio 2017**: Unicode 和 MBCS MFC Dll 使用安装**使用 c + + 桌面开发**当你选择的工作负荷**MFC 和 ATL 支持**从**可选组件**窗格。 如果你的安装不包括这些组件，你可以启动安装程序从**新项目**对话框，方法是使用**打开 Visual Studio 安装程序**链接。

## <a name="see-also"></a>请参阅

[MFC 库版本](../mfc/mfc-library-versions.md)

