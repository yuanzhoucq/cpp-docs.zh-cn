---
title: "/CLRTHREADATTRIBUTE（设置 CLR 线程特性） | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.CLRThreadAttribute"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/CLRTHREADATTRIBUTE 链接器选项"
  - "-CLRTHREADATTRIBUTE 链接器选项"
ms.assetid: 4907e9ef-5031-446c-aecf-0a0b32fae1e8
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /CLRTHREADATTRIBUTE（设置 CLR 线程特性）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

显式指定用于 CLR 程序的入口点的线程特性。  
  
## 语法  
  
```  
/CLRTHREADATTRIBUTE:{STA|MTA|NONE}  
```  
  
#### 参数  
 MTA  
 将 MTAThreadAttribute 特性应用于程序的入口点。  
  
 NONE  
 等同于不指定 \/CLRTHREADATTRIBUTE。让公共语言运行时\(CLR\)设置默认线程特性。  
  
 STA  
 将 STAThreadAttribute 特性应用于程序的入口点。  
  
## 备注  
 设置线程特性只有在生成 .exe 时才有效，因为它影响主线程的入口点。  
  
 如果使用默认入口点（例如 main 或 wmain），则使用 \/CLRTHREADATTRIBUTE 或将线程特性（STAThreadAttribute 或 MTAThreadAttribute）置于默认入口函数来指定线程模型。  
  
 如果使用非默认入口点，则先使用 \/CLRTHREADATTRIBUTE 或将线程特性置于非默认入口函数来指定线程模型，然后使用 [\/ENTRY](../../build/reference/entry-entry-point-symbol.md) 来指定非默认入口点。  
  
 如果在源代码中指定的线程模型与使用 \/CLRTHREADATTRIBUTE 指定的线程模型不一致，链接器将忽略 \/CLRTHREADATTRIBUTE 并应用在源代码中指定的线程模型。  
  
 例如，如果 CLR 程序承载使用单线程的 COM 对象，则必须使用单线程。如果 CLR 程序使用多线程，则该程序不能承载使用单线程的 COM 对象。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展开**“配置属性”**节点。  
  
3.  展开**“链接器”**节点。  
  
4.  选择**“高级”**属性页。  
  
5.  修改**“CLR 线程特性”**属性。  
  
### 以编程方式设置此链接器选项  
  
1.  请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRThreadAttribute%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)