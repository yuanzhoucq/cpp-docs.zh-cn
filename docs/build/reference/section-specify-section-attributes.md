---
title: "/SECTION（指定节特性） | Microsoft Docs"
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
  - "/section"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/SECTION 链接器选项"
  - "节特性"
  - "SECTION 链接器选项"
  - "-SECTION 链接器选项"
ms.assetid: 92b69d81-e421-462e-b46f-7d0dff9b9d16
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /SECTION（指定节特性）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/SECTION:name,[[!]{DEKPRSW}][,ALIGN=#]  
```  
  
## 备注  
 \/SECTION 选项将更改节的特性，以重写编译节的 .obj 文件时设置的特性。  
  
 可移植可执行 \(PE\) 文件中的节大致等效于新的可执行 \(NE\) 文件中的段或资源。  节包含代码或数据。  与段不同，节是连续内存的块，没有大小限制。  有些节包含程序声明和直接使用的代码或数据，而有些数据节是由链接器和库管理器 \(lib.exe\) 创建的，包含了对操作系统来说至关重要的信息。  有关 NE 文件的更多信息，请参见知识库文章“Executable\-File Header Format”\(Q65122\)。  可在 MSDN 库 或 [http:\/\/search.support.microsoft.com](http://support.microsoft.com) 上找到知识库文章。  
  
 指定冒号 \(:\) 和节 *name*。  *name* 区分大小写。  
  
 不要使用以下名称，因为它们与标准名称冲突。  例如，.sdata 用在 RISC 平台上：  
  
-   .arch  
  
-   .bss  
  
-   .data  
  
-   .edata  
  
-   .idata  
  
-   .pdata  
  
-   .rdata  
  
-   .reloc  
  
-   .rsrc  
  
-   .sbss  
  
-   .sdata  
  
-   .srdata  
  
-   .text  
  
-   .xdata  
  
 为节指定一个或多个特性。  以下列出的特性字符不区分大小写。  必须指定您希望节具有的所有特性；省略的特性字符将导致该特性位被关闭。  如果不指定 R、W 或 E，则现有的读、写或可执行状态保持不变。  
  
 若要取反特性，请在特性字符前使用一个感叹号 \(\!\)。  特性字符的含义如下所示：  
  
|字符|特性|含义|  
|--------|--------|--------|  
|E|执行|节是可执行的|  
|R|Read|允许对数据进行读取操作|  
|W|写入|允许对数据进行写操作|  
|S|Shared|在所有加载图像的进程中共享节|  
|D|Discardable|将节标记为可放弃|  
|K|Cacheable|将节标记为不可缓存|  
|P|Pageable|将节标记为不可分页|  
  
 K 和 P 比较特殊，因为与其对应的节标志表示相反的含义。  如果在 .text 节 \(\/SECTION:.text,K\) 上指定它们之中的一个，当运行带 [\/HEADERS](../../build/reference/headers.md)选项 [Dumpbin](../../build/reference/dumpbin-options.md)时在节标志中将没有区别；它已被隐式缓存了。  若要移除默认值，请指定 \/SECTION:.text,\!K，DUMPBIN 将显示节特性，包括“未缓存。”。  
  
 没有设置 E、R 或 W 的 PE 文件中的节可能无效。  
  
 ALIGN*\=\#* 使您得以为特定的节指定对齐值。  有关更多信息，请参见 [\/ALIGN](../../build/reference/align-section-alignment.md)。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击**“命令行”**属性页。  
  
4.  将该选项键入**“附加选项”**框中。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)