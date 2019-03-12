---
title: ATL 程序或控件的源文件和头文件
ms.date: 11/04/2016
helpviewer_keywords:
- file types [C++], ATL source and headers
ms.assetid: cb65372f-4880-4007-b582-a52eaa568fd1
ms.openlocfilehash: 9a99c3c23a79c37e90d9a041f051cfeaaff13ae2
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57745017"
---
# <a name="atl-program-or-control-source-and-header-files"></a>ATL 程序或控件的源文件和头文件

根据为创建的项目选择的选项，在 Visual Studio 中创建 ATL 项目时会创建以下文件。

所有这些文件都位于 Projname 目录中，并位于解决方案资源管理器中的头文件（.h 文件）文件夹或源文件（.cpp 文件）文件夹中。

|文件名|说明|
|---------------|-----------------|
|projname.h|主包含文件，其中包含 C++ 接口定义和在 ATLSample.idl 中定义的项的 GUID 声明。 它是由 MIDL 在编译期间重新生成的。|
|Projname.cpp|主程序源文件。 它包含实现进程内服务器的 DLL 的导出和实现本地服务器的 `WinMain`。 对于服务，它还实现所有服务管理函数。|
|Resource.h|资源文件的头文件。|
|StdAfx.cpp|包括 StdAfx.h 和 Atlimpl.cpp 文件。|
|StdAfx.h|包括 ATL 头文件。|

## <a name="see-also"></a>请参阅

[为 Visual C++ 项目创建的文件类型](../ide/file-types-created-for-visual-cpp-projects.md)<br>
[MFC 程序或控件的源文件和头文件](../ide/mfc-program-or-control-source-and-header-files.md)<br>
[CLR 项目](../ide/files-created-for-clr-projects.md)
