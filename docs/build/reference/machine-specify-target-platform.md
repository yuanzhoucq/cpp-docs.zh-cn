---
title: "/MACHINE（指定目标平台） | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.TargetMachine"
  - "/machine"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/MACHINE 链接器选项"
  - "MACHINE 链接器选项"
  - "-MACHINE 链接器选项"
  - "映射文件, 创建链接器"
  - "目标平台"
ms.assetid: 8d41bf4b-7e53-4ab9-9085-d852b08d31c2
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /MACHINE（指定目标平台）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/MACHINE:{ARM|EBC|X64|X86}  
```  
  
## 备注  
 \/MACHINE 选项指定程序的目标平台。  
  
 通常，不需要指定 \/MACHINE 选项。  LINK 从 .obj 文件中推断出计算机类型。  但在某些情况下，LINK 无法确定计算机类型并发出[链接器工具错误 LNK1113](../../error-messages/tool-errors/linker-tools-error-lnk1113.md)。  如果发生了此类错误，请指定 \/MACHINE。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击**“高级”**属性页。  
  
4.  修改“目标计算机”属性。  
  
### 以编程方式设置此链接器选项  
  
1.  请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TargetMachine%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)