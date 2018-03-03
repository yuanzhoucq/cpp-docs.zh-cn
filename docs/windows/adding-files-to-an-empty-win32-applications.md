---
title: "将文件添加到空的 Win32 应用程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- empty projects, adding files
- projects [C++], adding items
- blank projects
- files [C++], adding to projects
ms.assetid: 070098e8-0396-49fe-a697-3daa2f1be6de
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8b3c5df80b9344b4a37d8296dc57b96cfb4f35c8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="adding-files-to-an-empty-win32-applications"></a>向空的 Win32 应用程序添加文件
### <a name="to-add-your-files-to-an-empty-windows-desktop-application"></a>向空的 Windows 桌面应用程序添加文件  
  
1.  在“解决方案资源管理器” 中选择目录。  
  
2.  右键单击目录名称，在快捷菜单中单击“添加”  ，然后单击“现有项” 。  
  
3.  在“添加现有项”对话框中 ，导航到想要添加到项目中的文件。  
  
4.  单击 **“确定”**。  
  
 要向项目中添加既不是源文件、头文件也不是资源文件的文件，请右键单击解决方案资源管理器中的解决方案节点，然后以相同的方法将文件添加到项目中。 将创建杂项文件夹来保存项目中的其他文件。  
  
> [!NOTE]
>  在生成项目之前，需要指定这些文件的生成选项，以便将文件正确地添加到已完成的应用程序中。 有关详细信息，请参阅 [通过属性页指定项目设置](../ide/property-pages-visual-cpp.md) 和 [生成 C/C++ 程序](../build/building-c-cpp-programs.md)。  
  
## <a name="see-also"></a>请参阅  
 [创建空的 Windows 桌面应用程序](../windows/creating-an-empty-windows-desktop-application.md)   
 [部署应用程序](http://msdn.microsoft.com/en-us/4ff8881d-0daf-47e7-bfe7-774c625031b4)