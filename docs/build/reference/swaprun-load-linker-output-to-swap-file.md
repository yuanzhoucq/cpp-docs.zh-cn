---
title: "/SWAPRUN（将链接器输出加载到交换文件） | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.SwapRunFromNet"
  - "/swaprun"
  - "VC.Project.VCLinkerTool.SwapRunFromCD"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/SWAPRUN 链接器选项"
  - "文件 [C++], LINK"
  - "LINK 工具 [C++], 输出"
  - "链接器 [C++], 将输出复制到交换文件"
  - "输出文件, 链接器"
  - "链接器输出的交换文件"
  - "SWAPRUN 链接器选项"
  - "-SWAPRUN 链接器选项"
ms.assetid: 4a1e7f46-4399-4161-8dfc-d6a71beaf683
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /SWAPRUN（将链接器输出加载到交换文件）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/SWAPRUN:{NET|CD}  
```  
  
## 备注  
 \/SWAPRUN 选项告知操作系统首先将链接器输出复制到一个交换文件，然后从该文件中运行映像。  这是 Windows NT 4.0 \(及更高版本\)的一项功能。  
  
 如果指定 NET，则操作系统首先将二进制文件映像从网络位置复制到一个交换文件，然后从该文件中加载该映像。  此选项对通过网络运行应用程序的情况非常有用。  当指定 CD 时，操作系统将把可移动磁盘上的图像复制到页面文件上然后再加载它。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击“系统”属性页。  
  
4.  修改下列任一属性：  
  
    -   **从 CD 交换运行**  
  
    -   **从网络交换运行**  
  
### 以编程方式设置此链接器选项  
  
1.  请参见 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SwapRunFromCD%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SwapRunFromNet%2A> 属性。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)