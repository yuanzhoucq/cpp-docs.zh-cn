---
title: "从现有代码的源文件 （Visual c + +） 的新项目 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.importwiz.location
dev_langs: C++
ms.assetid: 29ddffb9-5918-4d72-8c7a-a365f9de96dd
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 04f73f89745f797658029eac2331d1764af4c065
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="specify-project-location-and-source-files-create-new-project-from-existing-code-files-wizard"></a>“从现有代码文件创建新项目”向导 ->“指定项目位置和源文件”
从现有代码文件创建新项目向导的此页用于指定：  
  
-   新项目的目录路径  
  
-   要搜索现有的源文件的目录  
  
-   类型的向导将导入到新的项目的文件  
  
## <a name="task-list"></a>任务列表  
 [如何：通过现有代码创建 C++ 项目](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## <a name="uielement-list"></a>UIElement 列表  
 **项目文件位置**  
 指定新项目的目录路径。 此位置是所有的文件 （和子目录） 的新项目向导将放入其中。  
  
 **浏览**  
 显示**项目文件位置**对话框中，这可帮助您指定将包含新的项目的目录。 此控制，你可以导航到所需的文件夹。  
  
 **项目名称**  
 指定新项目的名称。 项目文件，具有文件扩展，如.vcxproj 将采用此名称。 现有代码文件将保留其原始名称。  
  
 **从这些文件夹将文件添加到项目**  
 选中之后，设置向导将现有代码文件从其原始指定的目录 （此控件下面的列表框中） 复制到新的项目。  
  
 **添加子文件夹**  
 指定将代码文件从目录的所有子目录复制列出**文件夹**到新的项目的列。  
  
 **文件夹**  
 指示包含要复制到新的项目的现有代码文件的目录的路径。 此列列出向导将搜索现有代码文件的所有目录。  
  
 **添加**  
 显示**从此文件夹将文件添加到项目**对话框中，可帮助你向导将搜索现有代码文件的指定目录。  
  
 **移除**  
 删除在此控件左侧的列表框中选择的目录路径。  
  
 **要向项目中添加的文件类型**  
 指定该向导将添加到新项目基于给定的文件扩展名的文件的类型。 文件扩展名前面加上星号通配符，和由分号分隔的文件扩展名的列表中。  
  
 **在解决方案资源管理器中显示所有文件**  
 指定在新项目在解决方案资源管理器窗口中是可见且显示中的所有文件。 默认情况下会启用此选项。