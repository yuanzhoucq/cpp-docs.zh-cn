---
title: "/WINMDFILE（指定 winmd 文件） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.GenerateWindowsMetadataFile"
dev_langs: 
  - "C++"
ms.assetid: 062b41b3-14d6-432c-a361-fdb66e918931
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# /WINMDFILE（指定 winmd 文件）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定由 [\/WINMD](../../build/reference/winmd-generate-windows-metadata.md) 链接器选项生成的 Windows 运行时元数据 \(winmd\) 输出文件的文件名。  
  
```  
  
/WINMDFILE:filename  
  
```  
  
## 备注  
 使用 `filename` 指定的值重写默认的 .winmd 文件名的值 \(`binaryname`.winmd\)。  注意不追加“.winmd”设置为 `filename`。 如果**\/WINMDFILE** 命令行列出多个值，则以最后一次优先。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择 **Linker** 文件夹。  
  
3.  选择**“Windows 元数据”**属性页。  
  
4.  在**Windows 元数据文件** 框中，输入 文件位置。  
  
## 请参阅  
 [\/WINMD（生成 Windows 元数据）](../../build/reference/winmd-generate-windows-metadata.md)   
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)