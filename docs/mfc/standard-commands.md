---
title: "标准命令 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- File menu
- identifiers [MFC], command IDs
- command IDs, standard commands
- OLE commands
- commands [MFC], standard
- standard command IDs
- Window menu commands
- standard commands
- View menu commands
- Edit menu standard commands
- Help [MFC], menus
- programmer-defined IDs [MFC]
ms.assetid: 88cf3ab4-79b3-4ac6-9365-8ac561036fbf
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bbdb763b2d7da04267a195e5d534da9528f2b74d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="standard-commands"></a>标准命令
框架定义许多标准命令消息。 这些命令的 ID 通常采用以下形式：  
  
 **ID_** *源*_*项*  
  
 其中*源*通常是菜单名称和*项*为菜单项。 例如，“文件”菜单上“新建”命令的命令 ID 为 `ID_FILE_NEW`。 标准命令 ID 将以粗体类型显示在文档中。 程序员定义的 ID 将以不同于周围文本的字体显示。  
  
 下面是支持的部分最重要的命令的列表：  
  
 *文件菜单命令*  
 新建、打开、关闭、保存、另存为、页面设置、打印设置、打印、打印预览、退出和最近使用的文件。  
  
 *编辑菜单命令*  
 清除、全部清除、复制、剪切、查找、粘贴、重复、替换、全选、撤消和重做。  
  
 *“视图”菜单命令*  
 工具栏和状态栏。  
  
 *“窗口”菜单命令*  
 新建、排列、层叠、水平平铺、垂直平铺和拆分。  
  
 *“帮助”菜单命令*  
 “索引”、“使用帮助”和“关于”。  
  
 *OLE 命令 （编辑菜单）*  
 插入新对象、 编辑链接、 粘贴链接、 选择性粘贴和*typename*对象 （谓词命令）。  
  
 框架将为这些命令提供各种级别的支持。 一些命令仅作为定义的命令 ID 支持，而其他命令则通过实现支持。 例如，框架通过新建文档对象，显示一个“打开”对话框并打开和读取文件来实现“文件”菜单上的“打开”命令。 与此相反，则必须在编辑菜单上的命令自行实现，因为等命令**ID_EDIT_COPY**取决于要复制的数据的性质。  
  
 有关支持的命令的详细信息和提供实现的级别，请参阅[技术说明 22](../mfc/tn022-standard-commands-implementation.md)。 标准命令是在文件 AFXRES.H. 中定义的。  
  
## <a name="see-also"></a>请参阅  
 [用户界面对象和命令 ID](../mfc/user-interface-objects-and-command-ids.md)

