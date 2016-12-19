---
title: "/NOENTRY（无入口点） | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.ResourceOnlyDLL"
  - "/noentry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/NOENTRY 链接器选项 [C++]"
  - "DLL [C++], 创建"
  - "入口点 [C++], 链接器指定"
  - "NOENTRY 链接器选项"
  - "-NOENTRY 链接器选项"
  - "纯资源 DLL [C++], 创建"
ms.assetid: 0214dd41-35ad-43ab-b892-e636e038621a
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /NOENTRY（无入口点）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/NOENTRY  
```  
  
## 备注  
 \/NOENTRY 选项是创建不包含可执行代码的纯资源 DLL 所必需的。  有关详细信息，请参阅 [创建纯资源 DLL](../../build/creating-a-resource-only-dll.md)。  
  
 请使用此选项防止 LINK 将 `_main` 的引用链接到 DLL 中。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”对话框。  有关详细信息，请参阅[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择“链接器”文件夹。  
  
3.  选择“高级”属性页。  
  
4.  修改“无入口点”属性。  
  
### 以编程方式设置此链接器选项  
  
1.  请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ResourceOnlyDLL%2A>。  
  
## 请参阅  
 [创建纯资源 DLL](../../build/creating-a-resource-only-dll.md)   
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)