---
title: "/WINMDKEYCONTAINER（指定密钥容器） | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.WINMDKEYCONTAINER"
dev_langs: 
  - "C++"
ms.assetid: c2fc44dc-7cb5-42b9-897f-1b124928f2f7
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /WINMDKEYCONTAINER（指定密钥容器）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定用于对 Windows 元数据\(.winmd\)文件进行签名的密钥容器。  
  
```  
  
/WINMDKEYCONTAINER:name  
  
```  
  
## 备注  
 类似于应用到中的 [\/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md) \(链接器选项 .winmd\) 文件。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择 **Linker** 文件夹。  
  
3.  选择**“Windows 元数据”**属性页。  
  
4.  在**Windows 元数据关键文件** 框中，输入文件位置。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)