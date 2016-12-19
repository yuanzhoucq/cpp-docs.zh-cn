---
title: "/MAP（生成映射文件） | Microsoft Docs"
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
  - "/map"
  - "VC.Project.VCLinkerTool.MapFileName"
  - "VC.Project.VCLinkerTool.GenerateMapFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/MAP 链接器选项"
  - "生成映射文件链接器选项"
  - "MAP 链接器选项"
  - "-MAP 链接器选项"
  - "映射文件链接器选项"
  - "映射文件, 创建链接器"
  - "映射文件, 有关正被链接的程序的信息"
  - "映射文件, 指定文件名"
ms.assetid: 9ccce53d-4e36-43da-87b0-7603ddfdea63
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /MAP（生成映射文件）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/MAP[:filename]  
```  
  
## 备注  
 其中：  
  
 *filename*  
 用户指定的映射文件的名称。  该名称将会替换默认名称。  
  
## 备注  
 \/MAP 选项告知链接器创建映射文件。  
  
 默认情况下，链接器用程序的基名称和扩展名 .map 命名映射文件。  可选的*文件名* 使您得以重写映射文件的默认名称。  
  
 映射文件是一个文本文件，包含有关被链接程序的下列信息：  
  
-   模块名称，为文件的基名称  
  
-   时间戳，来自程序文件头（不是来自文件系统）  
  
-   程序中的组列表，包括每个组的起始地址（*节*:*偏移量*的形式）、长度、组名和类  
  
-   公共符号的列表，包括每个地址（*节*:*偏移量*的形式）、符号名称、平直地址和包含符号定义的 .obj 文件  
  
-   入口点（*节*:*偏移量*的形式）  
  
 [\/MAPINFO](../../build/reference/mapinfo-include-information-in-mapfile.md) 选项指定要包括在映射文件中的附加信息。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击“调试”属性页。  
  
4.  修改“生成映射文件”属性。  
  
### 以编程方式设置此链接器选项  
  
1.  请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateMapFile%2A>和<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MapFileName%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)