---
title: "/HEAP（设置堆大小） | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.HeapCommitSize"
  - "/heap"
  - "VC.Project.VCLinkerTool.HeapReserveSize"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/HEAP 链接器选项"
  - "堆分配, 设置堆大小"
  - "HEAP 链接器选项"
  - "-HEAP 链接器选项"
ms.assetid: a3f71927-7f1d-492c-9fdb-dfccb1a043da
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /HEAP（设置堆大小）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/HEAP:reserve[,commit]  
```  
  
## 备注  
 \/HEAP 选项设置堆的大小（以字节为单位）。  此选项仅在生成 .exe 文件时使用。  
  
 *reserve* 参数指定虚拟内存中总的堆分配。  默认堆大小为 1 MB。  链接器将指定值向上舍入为最接近的 4 个字节。  
  
 可选 `commit` 参数取决于操作系统的解释。  在 Windows NT\/Windows 2000 中，它指定一次分配的物理内存的数量。  提交的虚拟内存导致空间被保留在页面文件中。  更高的 `commit` 值在应用程序需要更多堆空间时可节省时间，但会增加内存需求并有可能延长启动时间。  
  
 以十进制或 C 语言表示法指定 *reserve* 值和 `commit` 值。  
  
 通过带 [HEAPSIZE](../../build/reference/heapsize.md) 的模块定义文件也可以实现该功能。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击“系统”属性页。  
  
4.  修改“堆提交大小”属性。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapReserveSize%2A>和<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapCommitSize%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)