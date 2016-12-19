---
title: "/VERSION（版本信息） | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.Version"
  - "/version"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/VERSION 链接器选项"
  - "“版本信息”链接器选项"
  - "VERSION 链接器选项"
  - "-VERSION 链接器选项"
  - "版本号, 在 .exe 中指定"
ms.assetid: b86d0e86-dca6-4316-aee2-d863ccb9f223
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /VERSION（版本信息）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/VERSION:major[.minor]  
```  
  
## 备注  
 其中：  
  
 *major* 和 *minor*  
 希望 .exe 或 .dll 文件头中包含的版本号。  
  
## 备注  
 \/VERSION 选项告知链接器将版本号置于 .exe 或 .dll 文件头中。  使用 DUMPBIN [\/HEADERS](../../build/reference/headers.md) 查看 OPTIONAL HEADER VALUES 的图像版本字段，以查看 \/VERSION 的效果。  
  
 *major* 和 *minor* 参数为 0 到 65,535 范围之间的十进制数。  默认值为版本 0.0。  
  
 用 \/VERSION 指定的信息不影响在 Windows 文件资源管理器中查看应用程序属性时所显示的应用程序的版本信息。  该版本信息来自用于生成应用程序的资源文件。  有关更多信息，请参见[版本信息编辑器](../../mfc/version-information-editor.md)。  
  
 另一种插入版本号的方法是用 [VERSION](../../build/reference/version-c-cpp.md) 模块定义语句。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击**“常规”**属性页。  
  
4.  修改**“版本”**属性。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Version%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)