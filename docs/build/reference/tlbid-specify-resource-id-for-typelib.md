---
title: "/TLBID（指定类型库的资源 ID） | Microsoft Docs"
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
  - "/tlbid"
  - "VC.Project.VCLinkerTool.TypeLibraryResourceID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".tlb 文件, 指定资源 ID"
  - "/TLBID 链接器选项"
  - "tlb 文件, 指定资源 ID"
  - "TLBID 链接器选项"
  - "-TLBID 链接器选项"
  - "类型库, 指定资源 ID"
ms.assetid: 434b28a2-4656-4d52-ac82-8b18bf486fb2
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /TLBID（指定类型库的资源 ID）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/TLBID:id  
```  
  
## 备注  
 其中：  
  
 `id`  
 链接器创建的类型库的用户指定值。  它重写值为 1 的默认资源 ID。  
  
## 备注  
 当编译使用特性的程序时，链接器将创建类型库。  链接器将把值为 1 的资源 ID 分配给类型库。  
  
 如果该资源 ID 与现有资源中的一个冲突，则可以用 \/TLBID 指定另一个 ID。  可以传递给 `id` 的值范围是 1 到 65535。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击“嵌入的 IDL”属性页。  
  
4.  修改“类型库资源 ID”属性。  
  
### 以编程方式设置此链接器选项  
  
1.  请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryResourceID%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)