---
title: "/DYNAMICBASE（使用地址空间布局随机化功能） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.RandomizedBaseAddress"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DYNAMICBASE 链接器选项"
  - "DYNAMICBASE 链接器选项"
  - "-DYNAMICBASE 链接器选项"
ms.assetid: 6c0ced8e-fe9c-4b63-b956-eb8a55fbceb2
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /DYNAMICBASE（使用地址空间布局随机化功能）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] 的地址空间布局随机化 \(ASLR\) 功能，指定是否生成可在加载时随机重新设定基址的可执行文件映像。  
  
## 语法  
  
```  
/DYNAMICBASE[:NO]  
```  
  
## 备注  
 默认情况下，\/DYNAMICBASE 处于打开状态。  
  
 此选项修改可执行文件头，以指示是否应在加载时对应用程序随机重新设定基址。  
  
 [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] 支持地址空间布局随机化功能。  
  
### 在 Visual Studio 中设置此链接器选项  
  
1.  打开此项目的**“属性页”**对话框。  有关详细信息，请参阅[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展开**“配置属性”**节点。  
  
3.  展开**“链接器”**节点。  
  
4.  选择**“高级”**属性页。  
  
5.  修改**“随机基址”**属性。  
  
### 以编程方式设置此链接器选项  
  
1.  请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RandomizedBaseAddress%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)