---
title: "TN023：标准 MFC 资源 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.resources"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "资源 [MFC]"
  - "标准资源"
  - "TN023"
ms.assetid: 60af8415-c576-4c2f-a711-ca5da0b9a1f2
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN023：标准 MFC 资源
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此注释说明 MFC 库提供和所需的标准资源。  
  
## TN023：标准 MFC 资源  
 MFC 提供可在应用程序中使用预定义资源的两类：CLIPART 资源和标准框架资源。  
  
 CLIPART 资源是附加资源可能需要向应用程序的用户界面中以框架不确定，但是。  CLIPART 以下资源示例 [CLIPART](../top/visual-cpp-samples.md)包含该泛型：  
  
-   Common.rc:包含资源的单个文件：  
  
    -   代表各种业务和数据操作任务图标的大型集合。  
  
    -   若干常用 Afxres.rc 光标 \(请参见\)。  
  
    -   包含多个工具栏按钮的工具栏位图。  
  
    -   使用 Commdlg.dll 的位图和图标资源。  
  
-   Indicate.rc:状态栏包含键状态指示器的字符串资源，如“”和 Caps Lock 的。  
  
-   Prompts.rc:包含菜单提示每个预定义命令的字符串资源，例如“创建新文档”的 `ID_FILE_NEW`。  
  
-   Commdlg.rc:包含标准 COMMDLG 对话框模板的 Visual C\+\+ 兼容 .rc 文件。  
  
 标准框架资源与 AFX 定义的资源 ID 的框架为内部实现依赖于。  基本上不需要更改这些 AFX 定义的资源。  如果，则应按本主题后面所述的过程。  
  
 以下资源包含\\INCLUDE MFC 框架在目录：  
  
-   Afxres.rc:框架使用的通用资源。  
  
-   Afxprint.rc:资源特定对打印。  
  
-   Afxolecl.rc:OLE 资源特定于客户端应用程序。  
  
-   Afxolev.rc:资源特定于完整的 OLE 服务器应用程序。  
  
## CLIPART 使用资源  
  
#### CLIPART 使用二进制资源  
  
1.  打开在 Visual C\+\+ 应用程序中的资源文件。  
  
2.  打开 Common.rc。  此文件包含在任何二进制剪贴画资源。  因为 Common.rc 文件编译，这可能需要一些时间。  
  
3.  按住 Ctrl，在您拖动要从 Common.rc 使用到应用程序资源文件中的资源。  
  
 若要使用其他剪贴画资源，请执行相同的步骤。  唯一的差别是您打开相应的 .rc 文件而不是 Common.rc。  
  
> [!NOTE]
>  注意不永久无意中将资源从 Common.rc 外部。  如果按住 Ctrl 键，同时将资源时，您会创建副本。  如果不使保持 Ctrl 下，在您拖动时，资源将移动。  如果担心您可能偶尔对 Common.rc 文件的更改，请单击“不”，则会询问是否保存对 Common.rc 的更改时。  
  
> [!NOTE]
>  .rc 资源文件与特定资源 `TEXTINCLUDE` 将防止您意外保存 .rc 文件的顶部位于标准它们。  
  
### 自定义标准 Framework 资源  
 通过在应用程序的资源文件，中的 \#include 命令标准框架资源位于应用程序通常包括。  AppWizard 将生成一个资源文件。  此文件包含相应的标准框架资源，AppWizard 选项您选择。  可以查看，添加或移除的资源更改编译时指令中。  若要执行此操作，请打开 **资源** 菜单并选择 **包括文本**。  查看“编译时指令”编辑项。  例如：  
  
```  
#include "afxres.rc"  
#include "afxprint.rc"  
```  
  
 最常见的情况上自定义标准框架资源添加或移除其他与打印，OLE 的客户和 OLE 支持服务器中。  
  
 在某些少见的情况下您可能希望自定义标准框架特定资源的内容应用程序，而不只是添加和删除整个文件。  按步骤显示可如何限制包括的资源：  
  
##### 自定义标准资源文件的内容  
  
1.  打开在 Visual C\+\+ 资源的文件。  
  
2.  使用"资源包括命令，移除要自定义标准的 .rc 文件的 `#include`。  例如，打印预览自定义工具栏，请移除 `#include "afxprint.rc"` 行。  
  
3.  打开在\\INCLUDE 的相应的标准 MFC 资源文件。  在示例稍后在本主题前面，适当的是 MFC \\Include\\Aafxprint .rc 文件  
  
4.  复制所有资源从标准 .rc 文件添加到应用程序资源文件内。  
  
5.  修改标准资源的副本将应用程序资源的文件。  
  
> [!NOTE]
>  请勿修改资源直接在标准 .rc 文件。  执行此操作将修改资源可以在每个应用程序使用，而不仅仅是在当前工作的文件。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)