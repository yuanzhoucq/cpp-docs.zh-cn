---
title: "编辑版本信息资源中的字符串 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.editors.version
dev_langs:
- C++
helpviewer_keywords:
- version information resources
- resources [Visual Studio], editing version information
ms.assetid: d3a7d4e4-7d31-47c2-902c-f50b8404ba4f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5add7bfb11b1c416853bb10ddbb2956885e181ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="editing-a-string-in-a-version-information-resource"></a>编辑版本信息资源中的字符串
### <a name="to-edit-a-string-in-a-version-information-resource"></a>编辑版本信息资源中的字符串  
  
1.  单击相应项目一次以选择它，然后再次开始编辑它。 直接在版本信息表中或在 [“属性”窗口](/visualstudio/ide/reference/properties-window)中进行更改。 进行的更改会在这两个位置得到反映。  
  
     **注意** 在版本信息编辑器中编辑 **FILEFLAGS** 键时，你会注意到无法为 .rc 文件设置 **Debug**、 **Private Build**或 **Special Build** 属性（在“属性”窗口中）：  
  
    -   版本信息编辑器集会基于 **_DEBUG** 生成标志，在资源脚本中使用 #ifdef 设置 **Debug** 属性。  
  
    -   如果 **Private Build** 键在版本信息表中设置了 **Value** ，则 **FILEFLAGS** 键的对应 **Private Build** 属性（在“属性”窗口中为 **True**。 如果 **Value** 为空，则该属性为 **False**。 同样， **Special Build** 键（在版本信息表中）会与 **FILEFLAGS** 键的 **Special Build** 属性关联。  
  
 可以通过单击键或值列标题来对字符串块的信息序列进行排序。 这些标题会自动将信息重新排列为所选顺序。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中*.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
 **要求**  
  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [版本信息编辑器](../windows/version-information-editor.md)   
 [版本信息 (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)

