---
title: "/VERBOSE（打印进度消息） | Microsoft Docs"
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
  - "/verbose"
  - "VC.Project.VCLinkerTool.ShowProgress"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/VERBOSE 链接器选项"
  - "依赖项 [C++], 链接器输出中的依赖项信息"
  - "链接器 [C++], 输出依赖项信息"
  - "链接 [C++], 会话进度信息"
  - "“打印进度消息”链接器选项"
  - "VERBOSE 链接器选项"
  - "-VERBOSE 链接器选项"
ms.assetid: 9c347d98-4c37-4724-a39e-0983934693ab
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /VERBOSE（打印进度消息）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/VERBOSE[:{ICF|INCR|LIB|REF|SAFESEH|UNUSEDLIBS}]  
```  
  
## 备注  
 链接器将有关链接会话进度的信息发送到“输出”窗口。  在命令行上，信息被发送到标准输出，并可以重定向到文件。  
  
|选项|说明|  
|--------|--------|  
|\/VERBOSE|显示有关链接进度的详细信息。|  
|\/VERBOSE:ICF|显示关于从使用 [\/OPT:ICF](../../build/reference/opt-optimizations.md) 中产生的链接器活动结果的信息。|  
|\/VERBOSE:INCR|有关增量方式显示信息的链接。|  
|\/VERBOSE:LIB|显示进度消息，仅指示所搜索的库。<br /><br /> 所显示的信息包括库搜索进程，同时还列出每个库和对象名（包括完整路径），正从库中解析的符号，以及引用该符号的对象的列表。|  
|\/VERBOSE:REF|显示关于从使用 [\/OPT:REF](../../build/reference/opt-optimizations.md) 中产生的链接器活动结果的信息。|  
|\/VERBOSE:SAFESEH|显示与在未指定 [\/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md) 时哪些模块与安全异常处理不兼容的有关信息。|  
|\/VERBOSE:UNUSEDLIBS|这些图像生成时，显示有关不使用的任何库文件的信息。|  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  展开 **Linker** 文件夹。  
  
3.  选择**“命令行”**属性页。  
  
4.  在**“附加选项”**框中添加选项。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ShowProgress%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)