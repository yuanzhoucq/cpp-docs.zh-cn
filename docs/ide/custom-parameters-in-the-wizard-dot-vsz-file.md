---
title: "向导 .Vsz 文件中的自定义参数 | Microsoft Docs"
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
  - "ABSOLUTE_PATH 宏"
  - "自定义向导, .vsz 文件"
  - "HTML_FILTER 宏"
  - "HTML_PATH 宏"
  - "IMAGE_FILTER 宏"
  - "IMAGES_PATH 宏"
  - "MISC_FILTER 宏"
  - "PRODUCT 宏"
  - "PRODUCT_INSTALLATION_DIR 宏"
  - "PROJECT_TEMPLATE_NAME 宏"
  - "PROJECT_TEMPLATE_PATH 宏"
  - "RELATIVE_PATH 宏"
  - "SCRIPT_COMMON_PATH 宏"
  - "SCRIPT_FILTER 宏"
  - "SCRIPT_PATH 宏"
  - "START_PATH 宏"
  - "TEMPLATE_FILTER 宏"
  - "TEMPLATES_PATH 宏"
  - "WIZARD_NAME 宏"
  - "WIZARD_UI 宏"
ms.assetid: 560dd5c0-7cff-4974-b856-5ca25b0669b8
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 向导 .Vsz 文件中的自定义参数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

.vsz 文件的头两行标识向导版本和要共同创建的向导的 ProgID 或 CLSID。  .vsz 文件还可包括可选的上下文参数和自定义参数，这些参数与 HTML 符号节提供的符号一起添加到符号表中。  
  
 <xref:Microsoft.VisualStudio.VsWizard.VsWizardClass.Execute%2A> 方法显示向导，它将 .vsz 文件中定义的一系列上下文和自定义参数作为它的参数。  
  
 在 [.vsz 文件](../ide/dot-vsz-file-project-control.md)或 .htm 文件中，以下常用符号被指定为自定义参数，它们可用于向导 HTML、脚本或模板文件。  
  
## 示例  
 如下面的 .vsz 文件项所示，名为 MyProjWiz 的向导包含用户界面。  
  
```  
VSWIZARD 7.0  
Wizard=VsWizard.VsWizardEngine  
Param="WIZARD_NAME = MyProjWiz"  
Param="WIZARD_UI = TRUE"  
```  
  
### 向导 .vsz 文件中自定义参数的符号  
  
|符号|定义|  
|--------|--------|  
|ABSOLUTE\_PATH|向导文件的位置。|  
|HTML\_FILTER|在 .vsz 文件中指定。  放置在**解决方案资源管理器**的 HTML Files 文件夹中的文件类型。  通常指定为“htm”。|  
|HTML\_PATH|在 .vsz 文件中指定。  向导的 [HTML 文件](../ide/html-files.md)的位置。  默认情况下为 START\_PATH\\HTML\\*LANGUAGE*（其中 *LANGUAGE* 是系统注册表指定的区域设置）。 **Note:**  通过将 \<LangID\> 设置为 HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\7.0\\General\\UILanguage 的十进制值，可以指定其他语言。  有关更多信息，请参见[将向导本地化为多种语言](../ide/localizing-a-wizard-to-multiple-languages.md)。  有关十进制语言值的列表，请参见[其他语言的向导支持](../ide/wizard-support-for-other-languages.md)。|  
|IMAGE\_FILTER|在 .vsz 文件中指定。  放置在解决方案资源管理器的 Image Files 文件夹中的文件类型。  通常指定为“bmp;gif”。|  
|IMAGES\_PATH|在 .vsz 文件中指定。  html 文件中使用的图像文件的位置。  默认情况下为 START\_PATH\\Images。|  
|MISC\_FILTER|在 .vsz 文件中指定。  放置在解决方案资源管理器的 Misc 文件夹中的文件类型。  通常指定为“vsz;vsdir;ico;vcproj;csproj;css;inf”。|  
|PRODUCT|默认情况下设置为 Visual C\+\+；然而，可将该值设置为 Visual Basic 以创建 Visual Basic 向导，等等。|  
|PRODUCT\_INSTALLATION\_DIR|在注册表的 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\7.0\\Setup\\\<Product\>\\ProductDir 处列出的目录。|  
|PROJECT\_TEMPLATE\_NAME|在 .vsz 文件中指定。  向导用于创建项目的项目模板文件。  通常指定为“txt”。|  
|PROJECT\_TEMPLATE\_PATH|包含项目的[模板文件](../ide/template-files.md)的目录。  对于 Visual C\+\+，默认情况下为 PRODUCT\_INSTALLATION\_DIR\\VCWizards。|  
|RELATIVE\_PATH|如果未找到 ABSOLUTE\_PATH，则考虑使用 RELATIVE\_PATH。  这是相对于 PRODUCT\_INSTALLATION\_DIR 的路径。  对于 Visual C\+\+，RELATIVE\_PATH 为 PRODUCT\_INSTALLATION\_DIR\\VCWizards。|  
|SCRIPT\_COMMON\_PATH|相对于 PRODUCT\_INSTALLATION\_DIR 的目录名，在此处可找到公共脚本文件。  例如，对于 Visual C\+\+，它是 VCWizards。|  
|SCRIPT\_FILTER|在 .vsz 文件中指定。  放置在解决方案资源管理器的 Script Files 文件夹中的文件类型。  通常指定为“js”\(JScript\) 或“vbs”\(VBScript\)。|  
|SCRIPT\_PATH|向导的 [JScript 文件](../ide/jscript-file.md)的位置。  默认情况下为 START\_PATH\\Scripts。|  
|START\_PATH|在 .vsz 文件中指定。  它不是由用户设置，但在内部用于标识 RELATIVE\_PATH 或 ABSOLUTE\_PATH。  将向导名 \(WIZARD\_NAME\) 追加到该值。|  
|TEMPLATE\_FILTER|在 .vsz 文件中指定。  放置在解决方案资源管理器的 Template Files 文件夹中的文件类型。  通常指定为“txt”。|  
|TEMPLATES\_PATH|在 .vsz 文件中指定。  向导的模板文件的位置。  默认情况下为 START\_PATH\\Templates\\\<LangID\>。 **Note:**  有关 LangID 的更多信息，请参见 HTML\_PATH。|  
|WIZARD\_NAME|指定向导名。  位于 .vsz 中并由其余的符号使用。|  
|WIZARD\_UI|在 .vsz 文件中指定。  Boolean 值，指示向导是否包含用户界面。  如果包含用户界面，则指定 **TRUE**；如果不包含用户界面，则指定 **FALSE**。|  
  
## 请参阅  
 <xref:EnvDTE.IDTWizard.Execute%2A>   
 [为向导创建的文件](../ide/files-created-for-your-wizard.md)   
 [自定义向导](../ide/custom-wizard.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)