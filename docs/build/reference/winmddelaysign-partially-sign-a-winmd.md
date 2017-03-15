---
title: "/WINMDDELAYSIGN（对 winmd 进行部分签名） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.WINMDDelaySign"
dev_langs: 
  - "C++"
ms.assetid: 445cd602-62cb-400a-8e3a-4beb6572724d
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# /WINMDDELAYSIGN（对 winmd 进行部分签名）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将公钥部分启用签名 Windows 运行时元数据 \(.winmd\) 文件的文件中。  
  
```  
  
/WINMDDELAYSIGN[:NO]  
  
```  
  
## 备注  
 类似于应用到 .winmd 文件的 [\/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md) 链接器选项。  如果仅需要将公钥包含在.winmd文件中，则使用 **\/WINMDDELAYSIGN**。  默认情况下，操作指定 **\/WINMDDELAYSIGN:NO** 链接器，则为；即不 winmd 签名文件。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择 **Linker** 文件夹。  
  
3.  选择**“Windows 元数据”**属性页。  
  
4.  在 **Windows 元数据延迟签名** 下拉列表框，选择所需选项。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)