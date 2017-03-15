---
title: "/MANIFESTFILE（命名清单文件） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.ManifestFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/MANIFESTFILE 链接器选项"
  - "MANIFESTFILE 链接器选项"
  - "-MANIFESTFILE 链接器选项"
ms.assetid: befa5ab2-a9cf-4c9b-969a-e7b4a930f08d
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# /MANIFESTFILE（命名清单文件）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/MANIFESTFILE:filename  
```  
  
## 备注  
 \/MANIFESTFILE 允许您更改清单文件的默认名称。清单文件的默认名称是追加有 .manifest 的文件名。  
  
 如果不同时使用 [\/MANIFEST](../../build/reference/manifest-create-side-by-side-assembly-manifest.md) 进行链接，则 \/MANIFESTFILE 将无效。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展开**“配置属性”**节点。  
  
3.  展开**“链接器”**节点。  
  
4.  选择**“清单文件”**属性页。  
  
5.  修改**“清单文件”**属性。  
  
### 以编程方式设置此链接器选项  
  
1.  请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ManifestFile%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)