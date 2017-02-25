---
title: "/RELEASE（设置校验和） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/release"
  - "VC.Project.VCLinkerTool.SetChecksum"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/RELEASE 链接器选项"
  - "校验和设置"
  - "RELEASE 链接器选项"
  - "-RELEASE 链接器选项"
ms.assetid: 93bcadf4-29ac-4824-914b-6997e3751d22
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /RELEASE（设置校验和）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/RELEASE  
```  
  
## 备注  
 \/RELEASE 选项将在 .exe 文件头中设置校验和。  
  
 操作系统要求设备驱动程序的校验和。  为设备驱动程序的发布版本设置校验和，以确保与未来的操作系统兼容。  
  
 当指定 [\/SUBSYSTEM:NATIVE](../../build/reference/subsystem-specify-subsystem.md) 选项时，默认情况下设置 \/RELEASE 选项。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击“高级”属性页。  
  
4.  修改“设置校验和”属性。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SetChecksum%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)