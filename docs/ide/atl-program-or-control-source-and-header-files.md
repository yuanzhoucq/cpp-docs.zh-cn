---
title: "ATL 程序或控件的源文件和头文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: file types [C++], ATL source and headers
ms.assetid: cb65372f-4880-4007-b582-a52eaa568fd1
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3a13a4c6ddb74a6f63b5da1171a3d4360199b508
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="atl-program-or-control-source-and-header-files"></a>ATL 程序或控件的源文件和头文件
ATL 项目在 Visual Studio 中，根据你为创建的项目选择的选项创建时创建以下文件。  
  
 所有这些文件位于*Projname*目录中，而且标头文件 （.h 文件） 文件夹或解决方案资源管理器中的源代码文件 （.cpp 文件） 文件夹中。  
  
|文件名|描述|  
|---------------|-----------------|  
|*Projname*.h|包含 c + + 接口定义和 ATLSample.idl 中定义的项的 GUID 声明的主包含文件。 它是由 MIDL 重新生成在编译期间。|  
|*Projname*.cpp|主程序源文件。 它包含的 DLL 的导出的进程内服务器的实现和的实现`WinMain`对于本地服务器。 对于服务，它还实现所有服务管理功能。|  
|Resource.h|资源文件的标头文件。|  
|StdAfx.cpp|包括 StdAfx.h 和 Atlimpl.cpp 文件。|  
|StdAfx.h|包括 ATL 标头文件。|  
  
## <a name="see-also"></a>请参阅  
 [为 Visual C++ 项目创建的文件类型](../ide/file-types-created-for-visual-cpp-projects.md)   
 [MFC 程序或控件的源文件和头文件](../ide/mfc-program-or-control-source-and-header-files.md)   
 [CLR 项目](../ide/files-created-for-clr-projects.md)