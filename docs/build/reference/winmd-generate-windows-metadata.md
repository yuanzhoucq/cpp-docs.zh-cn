---
title: "/WINMD（生成 Windows 元数据） | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.GenerateWindowsMetadata"
dev_langs: 
  - "C++"
ms.assetid: bcfb4901-411e-4c9e-9f78-23028b6e5fcc
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /WINMD（生成 Windows 元数据）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

启用 Windows 运行时元数据文件的生成\(.winmd\)文件。  
  
```  
  
/WINMD[:{NO|ONLY}]  
```  
  
## 备注  
 \/WINMD  
 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用的默认设置。  链接器生成二进制可执行文件，并 .winmd 元数据文件。  
  
 \/WINMD:NO  
 链接器生成仅二进制可执行文件，但是，不是一 .winmd 文件。  
  
 \/WINMD:ONLY  
 链接器生成仅 .winmd 文件。不生成二进制执行文件。  
  
 默认情况下，`binaryname`.winmd 输出文件名的格式。  若要指定不同的文件名，请使用 [\/WINMDFILE](../../build/reference/winmdfile-specify-winmd-file.md) 选项。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择 **Linker** 文件夹。  
  
3.  选择**“Windows 元数据”**属性页。  
  
4.  在 **生成Windows 元数据** 下拉列表框，选择所需选项。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)