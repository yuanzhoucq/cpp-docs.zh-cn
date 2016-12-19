---
title: ".Vsz 文件（项目控制） | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".vsz 文件"
  - "自定义向导, .vsz 文件"
  - "自定义向导, 项目控件文件"
  - "文件 [C++], “自定义向导”创建的"
  - "vsz 文件"
ms.assetid: b8678fee-6795-46d1-9338-48b22d5e9207
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# .Vsz 文件（项目控制）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每个向导的起始点均为 .vsz 文件。  .vsz 文件是一个文本文件，确定要调用的向导和传递给向导的信息。  该文件包含两行标头，后跟要传递给向导的各种可选参数。  有关可选参数的列表，请参见[预定义自定义向导符号](../ide/custom-parameters-in-the-wizard-dot-vsz-file.md)。  
  
 下面的示例显示 .vsz 文件头：  
  
```  
VSWIZARD 7.0  
Wizard=VsWizard.VsWizardEngine.10.0  
Param="WIZARD_NAME = My AppWizard"  
```  
  
-   文件头的第一行指定模板文件格式的版本号。  可以将此数字指定为 `6.0`、`7.0` 或 `7.1`。  其他版本号均无效，使用其他号码会导致“格式无效”错误。  
  
-   第二行将 **Wizard** 变量设置为通过 Visual Studio 共同创建的向导的 ProgID。  ProgID 是 CLSID 的字符串表示形式，如 `VsWizard.VsWizardEngine.10.0`。  
  
     如果向导具有用户界面，则 ProgID 自动指定向导以实现 <xref:Microsoft.VisualStudio.VsWizard.IVCWizCtlUI>。  默认情况下，此界面的方法用于项目的 [.htm 文件](../ide/html-files.md)中。  您可以通过在 .htm 文件中使用此界面的方法，更改向导的行为。  有关更多信息，请参见 <xref:Microsoft.VisualStudio.VsWizard.VCWizCtl>，它是 <xref:Microsoft.VisualStudio.VsWizard.IVCWizCtlUI> 的 coclass。  
  
-   这两行的后面是可选参数的列表，这些参数允许 .vsz 文件将附加的自定义参数传递到向导。  每个值都将作为一个字符串元素传递到向导控件的 <xref:Microsoft.VisualStudio.VsWizard.VsWizardClass.Execute%2A> 方法中的变量数组中。  默认情况下，具有用户界面的向导产生以下默认参数：  
  
    ```  
    Param="START_PATH = <path to the wizard>"  
    Param="HTML_PATH = <path to the wizard's HTML file>"  
    Param="TEMPLATES_PATH = <path to the wizard's template file>"  
    Param="SCRIPT_PATH = <path to the wizard's script files>"  
    Param="IMAGES_PATH = <path to the wizard's images>"  
    ```  
  
     如果向导没有用户界面，则它不具有 `IMAGES_PATH` 参数，而是包含以下参数：  
  
    ```  
    Param="WIZARD_UI = FALSE"  
    Param="SOURCE_FILTER = txt"  
    ```  
  
-   .vsz 文件可以包含以下参数，这些参数指定 [Common.js](../ide/customizing-cpp-wizards-with-common-jscript-functions.md) 文件中的函数：  
  
    ```  
    Param="PREPROCESS_FUNCTION = CanAddATLClass"  
    Param="PREPROCESS_FUNCTION = CanAddMFCClass"  
    Param="PREPROCESS_FUNCTION = CanAddClass"  
    ```  
  
 向导通过调用函数 [CanAddATLClass](../ide/canaddatlclass.md)、[CanAddMFCClass](../ide/canaddmfcclass.md) 和 [CanAddClass](../ide/canaddclass.md) 确认 [Visual C\+\+ 代码模型](http://msdn.microsoft.com/zh-cn/dd6452c2-1054-44a1-b0eb-639a94a1216b)是否可用。  如果其中一个函数返回 **false**，则向导不启动。  
  
 通过将 .vsz 文件放置在 vcprojects 目录中，可以将向导添加到 Visual Studio 的**“新建项目”**对话框中的“模板”窗格。  默认情况下，“自定义向导”将 .vsz 文件写入此目录。  
  
> [!NOTE]
>  如果删除向导文件和目录，还必须从 vcprojects 目录中删除项目的 .vsz 文件、.vsdir 文件和 .ico 文件。  
  
## 请参阅  
 [为向导创建的文件](../ide/files-created-for-your-wizard.md)   
 [自定义向导](../ide/custom-wizard.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [Visual C\+\+ Wizard Model](http://msdn.microsoft.com/zh-cn/159395ac-33c7-47bf-ad42-4e1435ddc758)   
 [使用 .Vsdir 文件为“添加项”和“新建项目”对话框添加向导](../Topic/Adding%20Wizards%20to%20the%20Add%20Item%20and%20New%20Project%20Dialog%20Boxes%20by%20Using%20.Vsdir%20Files.md)   
 [设计向导](../ide/designing-a-wizard.md)