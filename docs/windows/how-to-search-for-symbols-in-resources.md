---
title: "如何： 搜索资源中的符号 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- symbols, finding
- resources [Visual Studio], searching for symbols
ms.assetid: 6efef8e8-d0d4-4c49-b895-314974e7791a
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 04b2bb47977a349bfd06dc6770aab80626395714
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-search-for-symbols-in-resources"></a>如何：在资源中搜索符号
### <a name="to-find-symbols-in-resources"></a>在资源中查找符号  
  
1.  从**编辑**菜单上，选择**查找符号**。  
  
2.  在[查找符号对话框](http://msdn.microsoft.com/en-us/63e93d9c-784f-418d-a76a-723da5ff5d96)中**查找内容**框中，从下拉列表中选择以前的搜索字符串或键入你想要 （例如 ID_ACCEL1） 查找的加速键。  
  
    > [!TIP]
    >  若要使用[正则表达式](/visualstudio/ide/using-regular-expressions-in-visual-studio)对于您的搜索，你必须使用[在文件中查找](/visualstudio/ide/reference/find-command)从**编辑**命令而不是**查找符号**命令。 若要启用正则表达式，你必须**使用： 正则表达式**复选框中选择[查找对话框](http://msdn.microsoft.com/en-us/dad03582-4931-4893-83ba-84b37f5b1600)。 然后，您可以单击右侧的向右箭头按钮**查找内容**框以显示正则搜索表达式列表。 当你从此列表中选择表达式时，它将替换中的搜索文本**查找内容**框。  
  
3.  选择任一**查找**选项。  
  
4.  单击**查找下一个**。  
  
    > [!NOTE]
    >  无法搜索字符串、快捷键或二进制资源中的符号。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中*.NET Framework 开发指南。* 。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息以及 [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6)。  
  
 **要求**  
  
 Win32  
  
## <a name="see-also"></a>另请参阅  
 [符号： 资源标识符](../windows/symbols-resource-identifiers.md)   
 [资源文件](../windows/resource-files-visual-studio.md)   
 [资源编辑器](../windows/resource-editors.md)