---
title: "/STACK（堆栈分配） | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.StackReserveSize"
  - "VC.Project.VCLinkerTool.StackCommitSize"
  - "/stack"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "STACK 链接器选项"
  - "-STACK 链接器选项"
  - "内存分配, 堆栈"
  - "/STACK 链接器选项"
  - "堆栈, 设置大小"
ms.assetid: 73283660-e4bd-47cc-b5ca-04c5d739034c
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /STACK（堆栈分配）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/STACK:reserve[,commit]  
```  
  
## 备注  
 \/STACK 选项设置堆栈的大小（以字节为单位）。  此选项仅在生成 .exe 文件时使用。  
  
 `reserve` 值指定虚拟内存中的总的堆栈分配。  对于 ARM、x86 和 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 计算机，默认堆栈大小为 1 MB。  
  
 `commit` 取决于操作系统所作的解释。  在 Windows WindowsRT 中，它指定一次分配的物理内存的数量。  提交的虚拟内存导致空间被保留在页面文件中。  更高的 `commit` 值在应用程序需要更多堆空间时可节省时间，但会增加内存需求并有可能延长启动时间。  对于 ARM 、x86 和 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 计算机，默认提交值为 4 KB。  
  
 以十进制或 C 语言表示法指定 `reserve`和 `commit` 值。  
  
 设置堆栈大小的另一种方法是使用模块定义 \(.def\) 文件中的 [STACKSIZE](../../build/reference/stacksize.md) 语句。  如果两者都指定，则 **STACKSIZE** 重写堆栈分配 \(\/STACK\) 选项。  可以使用 [EDITBIN](../../build/reference/editbin-reference.md) 工具在生成 .exe 文件之后更改堆栈大小。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择 **Linker** 文件夹。  
  
3.  选择“系统”属性页。  
  
4.  修改下列任一属性：  
  
    -   **堆栈提交大小**  
  
    -   **堆栈保留大小**  
  
### 以编程方式设置此链接器选项  
  
1.  请参见 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackCommitSize%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackReserveSize%2A> 属性。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)