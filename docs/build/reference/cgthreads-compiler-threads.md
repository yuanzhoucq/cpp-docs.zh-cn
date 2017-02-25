---
title: "/CGTHREADS（编译器线程） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/CGTHREADS 链接器选项"
  - "CGTHREADS 链接器选项"
  - "-CGTHREADS 链接器选项"
ms.assetid: 4b52cfdb-3702-470b-9580-fabeb1417488
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# /CGTHREADS（编译器线程）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

设置 cl.exe 线程数以在指定链接时代码生成后用于优化和代码生成。  
  
## 语法  
  
```  
/CGTHREADS:[1-8]  
```  
  
## 参数  
 数值  
 可供 cl.exe 使用的最大线程数，范围在 1 到 8 之间。  
  
## 备注  
 在指定链接时代码生成 \([\/LTCG](../../build/reference/ltcg-link-time-code-generation.md)\) 后，**\/CGTHREADS** 选项指定 cl.exe 以并行方式使用的最大线程数，用于编译的优化和代码生成阶段。  默认情况下，cl.exe 使用四个线程，如同 **\/CGTHREADS:4** 所指定。  如果有更多处理器内核可用，则较大的 `number` 值可以缩短生成时间。  
  
 可为生成指定多个级别的并行。  msbuild.exe 开关 **\/maxcpucount** 指定可并行运行的 MSBuild 进程数。  [\/MP（使用多个进程生成）](../../build/reference/mp-build-with-multiple-processes.md) 编译器标志指定可同时编译源文件的 cl.exe 进程数。  [\/cgthreads](../../build/reference/cgthreads-code-generation-threads.md) 编译器选项指定由每个 cl.exe 进程使用的线程数。  由于处理器只能同时运行与处理器内核数量相同的线程数，因此同时为所有这些选项指定较大的值将不起作用，而且还会起反作用。  有关如何以并行方式生成项目的详细信息，请参阅[并行生成多个项目](../Topic/Building%20Multiple%20Projects%20in%20Parallel%20with%20MSBuild.md)。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  依次选择**“配置属性”**、**“链接器”**文件夹。  
  
3.  选择**“命令行”**属性页。  
  
4.  修改**“附加选项”**属性以包含 **\/CGTHREADS:**`number`，其中 `number` 是介于1 到 8 之间的值，然后选择**“确定”**。  
  
### 以编程方式设置此链接器选项  
  
-   请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [链接器选项](../../build/reference/linker-options.md)   
 [设置链接器选项](../../build/reference/setting-linker-options.md)