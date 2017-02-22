---
title: "/Zm（指定预编译头的内存分配限额） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/zm"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pch 文件, 内存分配限制"
  - "/Zm 编译器选项 [C++]"
  - "cl.exe 编译器, 内存分配限制"
  - "内存分配, “内存分配限制”编译器选项"
  - "PCH 文件, 内存分配限制"
  - "预编译的头文件, 内存分配限制"
  - "“指定预编译头内存分配限制”编译器选项"
  - "Zm 编译器选项 [C++]"
  - "-Zm 编译器选项 [C++]"
ms.assetid: 94c77d5e-6672-46a7-92e0-3f69e277727d
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# /Zm（指定预编译头的内存分配限额）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

确定编译器分配的用于构造预编译头的内存量。  
  
## 语法  
  
```  
/Zmfactor  
```  
  
## 参数  
 `factor`  
 一个比例因子，确定编译器用于构造预编译头的内存量。  
  
 `factor` 参数是编译器定义的工作缓冲区的默认大小所占的百分比。  `factor` 的默认值是 100 \(%\)，但你可以指定更大或更小的数值。  
  
## 备注  
 在早期版本的 Visual C\+\+ 中，编译器使用几个离散堆，每个堆都有一定的限制。  当前，编译器可根据需要动态增加堆，最多可增加到总堆大小限制，并且只需要固定大小的缓冲区即可构造预编译头。  因此，很少需要 **\/Zm** 编译器选项。  
  
 如果在你使用 **\/Zm** 编译器选项时，编译器用完堆空间，并发出 [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) 错误消息，则你可能保留了太多的内存。  可考虑移除 **\/Zm** 选项。  如果编译器发出 [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md) 错误消息，则伴随的 [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md) 消息会指定你在使用 **\/Zm** 编译器选项重新编译时要使用的 `factor` 参数。  
  
 下表显示当你假定默认预编译头缓冲区的大小为 75 MB 时，`factor` 参数如何影响内存分配限制。  
  
|`factor` 的值|内存分配限制|  
|-----------------|------------|  
|10|7.5 MB|  
|100|75 MB|  
|200|150 MB|  
|1000|750 MB|  
|2000|1500 MB|  
  
## 设置内存分配限制的其他方式  
  
#### 在 Visual Studio 开发环境中设置 \/Zm 编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  在导航窗格中，依次选择**“配置属性”**、**“C\/C\+\+”**和**“命令行”**。  
  
3.  在**“附加选项”**框中输入 **\/Zm** 编译器选项。  
  
#### 以编程方式设置 \/Zm 编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)