---
title: "查找字符串 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.string
dev_langs: C++
helpviewer_keywords:
- strings [C++], searching
- strings [C++]
ms.assetid: c2497173-f356-4f77-97d6-f0ac41782510
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a66b5dd34aa21a2a0791ecbc71bfd4abcc90c4fa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="finding-a-string"></a>查找字符串
你可以搜索字符串表中的一个或多个字符串，然后使用[正则表达式](/visualstudio/ide/using-regular-expressions-in-visual-studio)与**在文件中查找**命令 (**编辑**菜单) 查找字符串的所有实例模式相匹配。  
  
### <a name="to-find-a-string-in-the-string-table"></a>若要在字符串表中查找字符串  
  
1.  通过双击图标中的将其打开字符串表[资源视图](../windows/resource-view-window.md)。  
  
    > [!NOTE]
    >  如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  上**编辑**菜单上，单击**查找和替换**，然后选择**查找**。  
  
3.  在**查找内容**框中，从下拉列表中选择以前的搜索字符串或键入你想要查找的字符串的标题文本或资源标识符。  
  
4.  选择任一**查找**选项。  
  
5.  单击**查找下一个**。  
  
    > [!TIP]
    >  若要在搜索文件时，请使用正则表达式，使用**在文件中查找**命令。 键入要与模式匹配，或单击右侧的按钮的正则表达式**查找内容**框以显示正则搜索表达式列表。 当你从此列表中选择表达式时，它将替换中的搜索文本**查找内容**框。 如果使用正则表达式，请确保**使用： 正则表达式**复选框处于选中状态。  
  
 有关将资源添加到托管项目 （那些针对公共语言运行时） 的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中*.NET Framework 开发指南。* 。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅 [演练：本地化 Windows 窗体](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5) 和 [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6)。  
  
 **要求**  
  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [字符串编辑器](../windows/string-editor.md)   

