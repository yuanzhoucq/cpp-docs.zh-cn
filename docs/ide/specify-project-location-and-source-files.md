---
title: 从现有代码新建项目 - 源文件 (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.appwiz.importwiz.location
dev_langs:
- C++
ms.assetid: 29ddffb9-5918-4d72-8c7a-a365f9de96dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d85a7b85996ed307596865a31d55cf4b119e5bd5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338690"
---
# <a name="specify-project-location-and-source-files-create-new-project-from-existing-code-files-wizard"></a>“从现有代码文件创建新项目”向导 ->“指定项目位置和源文件”
使用“从现有代码文件创建新项目文件”向导的此页指定：  
  
-   新项目的目录路径  
  
-   搜索现有源文件的目录  
  
-   向导将导入到新项目的文件类型  
  
## <a name="task-list"></a>任务列表  
 [如何：通过现有代码创建 C++ 项目](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## <a name="uielement-list"></a>UIElement 列表  
 **项目文件位置**  
 指定新项目的目录路径。 这是该向导放置所有新项目文件（和子目录）的位置。  
  
 **浏览**  
 显示“项目文件位置”对话框，有助于指定包含新项目的目录。 通过此控件，可导航到所需文件夹。  
  
 **项目名称**  
 指定新项目的名称。 具有文件扩展名（如.vcxproj）的项目文件将采用此名称。 现有代码文件将保留其原始名称。  
  
 **将文件从这些文件夹添加到项目中**  
 选中后，将向导设置为将现有代码文件从其原始目录（在此控件下的列表框中指定）复制到新项目中。  
  
 **添加子文件夹**  
 指定将代码文件从 Folder 列列出的目录的所有子目录复制到新项目中。  
  
 **文件夹**  
 指定包含要复制到新项目的现有代码文件的目录路径。 此列列出了向导将搜索现有代码文件的所有目录。  
  
 **添加**  
 显示“将文件从文件夹添加到项目”对话框，有助于指定向导将搜索现有代码文件的目录。  
  
 **移除**  
 删除在此控件左侧列表框中选中的目录路径。  
  
 **要添加到项目中的文件类型**  
 指定向导将添加到基于给定文件扩展名的新项目的文件类型。 文件扩展名前面带有星号通配符，并在文件扩展名列表中以分号隔开。  
  
 **在解决方案资源管理器中显示所有文件**  
 指定新项目中的所有文件都可见并在“解决方案资源管理器”窗口中显示。 默认情况下会启用此选项。