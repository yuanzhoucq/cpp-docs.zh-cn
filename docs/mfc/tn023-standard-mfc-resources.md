---
title: "TN023： 标准 MFC 资源 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.resources
dev_langs:
- C++
helpviewer_keywords:
- resources [MFC]
- TN023
- standard resources
ms.assetid: 60af8415-c576-4c2f-a711-ca5da0b9a1f2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6fded011fda52dfde46804b03699dc93469e5e32
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="tn023-standard-mfc-resources"></a>TN023：标准 MFC 资源
此注释将介绍 MFC 库随附的和需要的标准资源。  
  
## <a name="standard-resources"></a>标准资源  
 MFC 提供了可在应用程序中使用的两种预定义资源：剪贴画资源和标准框架资源。  
  
 剪贴画资源是框架并不依赖的、但您可能希望添加到应用程序的用户界面的附加资源。 以下剪贴画资源包含在 MFC 常规示例[剪贴画](../visual-cpp-samples.md):  
  
-   Common.rc：包含以下内容的单个资源文件：  
  
    -   代表各种业务和数据处理任务的图标的大型集合。  
  
    -   若干常用光标（请参阅 Afxres.rc）。  
  
    -   包含若干工具栏按钮的工具栏位图。  
  
    -   Commdlg.dll 使用的位图和图标资源。  
  
-   Indicate.rc：包含状态栏键状态指示符（如用于大写锁定的“CAP”）的字符串资源。  
  
-   Prompts.rc：包含每个预定义命令的菜单提示字符串资源，如 `ID_FILE_NEW` 的“创建新文档”。  
  
-   Commdlg.rc：包含标准 COMMDLG 对话框模板的与 Visual C++ 兼容的 .rc 文件。  
  
 标准框架资源是带有框架所依赖的由 AFX 定义的 ID 的资源，用于内部实现。 您很少需要更改这些 AFX 定义的资源。 如果您确实要更改，则应遵循本主题后面所述的过程。  
  
 以下框架资源包含在 MFC\INCLUDE 目录中：  
  
-   Afxres.rc：框架使用的公共资源。  
  
-   Afxprint.rc：专用于打印的资源。  
  
-   Afxolecl.rc：特定于的 OLE 客户端应用程序的资源。  
  
-   Afxolev.rc：特定于完整的 OLE 服务器应用程序的资源。  
  
## <a name="using-clip-art-resources"></a>使用剪贴画资源  
  
#### <a name="to-use-a-clip-art-binary-resource"></a>使用剪贴画二进制资源  
  
1.  在 Visual C++ 中打开应用程序的资源文件。  
  
2.  打开 Common.rc。 此文件包含所有二进制剪贴画资源。 这可能需要一些时间，因为 Common.rc 文件经过了编译。  
  
3.  在从 Common.rc 将要使用的资源拖动到应用程序的资源文件时按住 Ctrl。  
  
 若要使用其他剪贴画资源，请执行相同的步骤。 唯一的区别是您将打开相应的 .rc 文件而不是 Common.rc。  
  
> [!NOTE]
>  注意不要无意中将资源永久性移出 Common.rc。 如果在拖动资源时按住 Ctrl 键，您将创建一个副本。 如果在拖动时不按住 Ctrl，则会移动资源。 如果担心可能意外对 Common.rc 文件进行更改，当系统询问是否保存对 Common.rc 的更改时，请单击“否”。  
  
> [!NOTE]
>  .rc 资源文件包含一个特殊的 `TEXTINCLUDE` 资源，它将阻止您意外地在标准 .rc 文件的基础上进行保存。  
  
### <a name="customizing-standard-framework-resources"></a>自定义标准框架资源  
 通常通过在应用程序的资源文件中使用 #include 命令将标准框架资源包含在应用程序中。 AppWizard 将生成一个资源文件。 此文件包含相应的标准框架资源，具体取决于您选择的 AppWizard 选项。 您可以通过更改编译时指令来评审、添加或删除包含的资源。 若要执行此操作，打开**资源**菜单，然后选择**设置包括**。 查看“编译时指令”编辑项。 例如:  
  
```  
#include "afxres.rc"  
#include "afxprint.rc"  
```  
  
 自定义标准框架资源最常见的情况是添加或删除用于打印、OLE 客户端和 OLE 服务器支持的其他包含文件。  
  
 在某些罕见的情况下，您可能希望为特定应用程序自定义标准框架资源的内容，而不只是添加和删除整个文件。 以下步骤显示了如何限制包含的资源：  
  
##### <a name="to-customize-the-contents-of-a-standard-resource-file"></a>自定义标准资源文件的内容  
  
1.  在 Visual C++ 中打开资源文件。  
  
2.  使用“资源”->“设置包含文件”命令，为要自定义的标准 .rc 文件删除 `#include`。 例如，若要自定义打印预览工具栏，删除 `#include "afxprint.rc"` 行。  
  
3.  在 MFC\INCLUDE 中打开相应的标准资源文件。 根据本主题前面的示例，相应的文件是 MFC\Include\Aafxprint.rc  
  
4.  从标准 .rc 文件中将所有资源复制到应用程序资源文件。  
  
5.  在应用程序资源文件中修改标准资源的副本。  
  
> [!NOTE]
>  不要直接在标准 .rc 文件中修改资源。 这样做会修改每个应用程序中可用的资源，而不只是当前处理的应用程序中的资源。  
  
## <a name="see-also"></a>请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

