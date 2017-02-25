---
title: "标准命令 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "命令 ID, 标准命令"
  - "命令 [C++], 标准"
  - "编辑菜单标准命令"
  - "“文件”菜单"
  - "帮助, 菜单"
  - "标识符 [C++], 命令 ID"
  - "OLE 命令"
  - "程序员定义的 ID [C++]"
  - "标准命令 ID"
  - "标准命令"
  - "“视图”菜单命令"
  - "“窗口”菜单命令"
ms.assetid: 88cf3ab4-79b3-4ac6-9365-8ac561036fbf
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 标准命令
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

框架定义许多标准命令消息。  这些命令的 ID 通常采用形式：  
  
 **ID\_** *Source*\_*Item*  
  
 其中*源*通常是一个菜单名和*项目*是一个菜单项。  例如，新的命令 ID " File "菜单上有 `ID_FILE_NEW`。  标准命令 ID。粗体显示文档。  程序员定义的 ID。与周围文本不同的字体显示。  
  
 下面是的某些列表支持的最重要的命令：  
  
 *“文件”菜单命令*  
 新，打开，请关闭，保存，另存为页、设置、打印设置、打印、打印预览、退出和最近使用的文件。  
  
 *编辑菜单命令*  
 清晰，清除所有，复制个，剪切，找到，粘贴，重复，替换，其中选、撤消和重做。  
  
 *“视图”菜单命令*  
 工具栏和状态栏  
  
 *“窗口”菜单命令*  
 新，请安排，级联，平铺，水平平铺类别和拆分。  
  
 *“帮助”菜单命令*  
 使用帮助索引和关于。  
  
 *OLE编辑菜单命令*  
 插入新的对象，编辑链接，将链接粘贴，特定 *类型* 对象 \(和谓词命令\)。  
  
 框架使用这些命令提供不同级别的支持。  而其他支持的彻底的实现，这些支持命令，仅当定义命令 ID。  例如，框架通过创建新文档对象，显示一个"打开"对话框然后打开并读取文件实现在"文件"菜单中打开命令。  相反，必须实现在"编辑"菜单上的命令，因为与 **ID\_EDIT\_COPY** 的命令取决于要复制的数据的性质。  
  
 有关命令支持的和实现的更多信息，请参见级别提供的 [技术说明 22](../mfc/tn022-standard-commands-implementation.md)。  标准命令文件中 AFXRES.H. 定义。  
  
## 请参阅  
 [用户界面对象和命令 ID](../mfc/user-interface-objects-and-command-ids.md)