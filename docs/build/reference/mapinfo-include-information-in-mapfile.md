---
title: "/MAPINFO（包含映射文件中的信息） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.MapLines"
  - "VC.Project.VCLinkerTool.MapInfoFixups"
  - "VC.Project.VCLinkerTool.MapExports"
  - "/mapinfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/MAPINFO 链接器选项"
  - "MAPINFO 链接器选项"
  - "-MAPINFO 链接器选项"
ms.assetid: 533d2bce-f9b7-4fea-ae1c-0b4864c9d10b
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /MAPINFO（包含映射文件中的信息）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/MAPINFO:EXPORTS  
```  
  
## 备注  
 \/MAPINFO 选项通知链接器包含映射文件中指定的信息，如果指定 [\/MAP](../../build/reference/map-generate-mapfile.md) 选项，则创建该映射文件。EXPORTS 告知链接器包括导出的函数。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击“调试”属性页。  
  
4.  修改**“映射导出”**属性：  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MapExports%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)