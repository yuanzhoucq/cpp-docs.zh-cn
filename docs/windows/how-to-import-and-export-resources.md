---
title: 如何： 导入和导出资源 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vs.resvw.resource.importing
- vc.resvw.resource.importing
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio], exporting
- graphics [C++], exporting
- graphics [C++], importing
- resources [Visual Studio], importing
- bitmaps [C++], importing and exporting
- toolbars [C++], importing
- images [C++], importing
- toolbars [C++], exporting
- cursors [C++], importing and exporting
- images [C++], exporting
ms.assetid: 3c9329dc-dcb8-4edd-a600-78e3e572bd89
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9e526ab335436730f4132b5b7127ec9079432a4a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879173"
---
# <a name="how-to-import-and-export-resources"></a>如何：导入和导出资源
可以导入图形资源（位图、图标、光标和工具栏）、HTML 文件和自定义资源以便在 Visual C++ 中使用。 可以从 Visual C++ 项目导出相同类型的文件以分隔可以在开发环境外部使用的文件。  
  
> [!NOTE]
>  无法导入或导出资源类型（如加速器、对话框和字符串表），因为它们不是独立的文件类型。  
  
### <a name="to-import-an-individual-resource-into-your-current-resource-file"></a>将一个单独的资源导入到当前资源文件中  
  
1.  在[资源视图](../windows/resource-view-window.md)，右键单击资源脚本的节点 (*.rc) 文件您想要添加的资源。  
  
2.  单击**导入**快捷菜单上。  
  
3.  找到并选择位图 (.bmp)、图标 (.ico)、光标 (.cur)、Html 文件 (.htm) 或要导入的其他文件的文件名。  
  
4.  单击**确定**将资源添加到所选文件**资源**视图。  
  
    > [!NOTE]
    >  无论选择哪种特定资源类型，导入过程的工作方式都是相同的。 导入的资源会自动添加到该资源类型的正确节点。  
  
### <a name="to-export-a-bitmap-icon-or-cursor-as-a-separate-file-for-use-outside-of-visual-c"></a>导出位图、图标或光标作为单独的文件（以便在 Visual C++ 外部使用）  
  
1.  在**资源**视图中，右键单击你想要导出的资源。  
  
2.  单击**导出**快捷菜单上。  
  
3.  在**导出资源**对话框框中，接受当前文件名或键入一个新。  
  
4.  导航到你想要保存该文件并单击的文件夹**导出**。  
  

  
 要求  
  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [资源文件](../windows/resource-files-visual-studio.md)   
 [资源编辑器](../windows/resource-editors.md)