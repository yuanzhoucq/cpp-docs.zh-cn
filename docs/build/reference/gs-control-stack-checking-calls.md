---
title: "/Gs（控制堆栈检查调用） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/GS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/GS 编译器选项 [C++]"
  - "禁用堆栈探测"
  - "GS 编译器选项 [C++]"
  - "-GS 编译器选项 [C++]"
  - "堆栈检查调用"
  - "堆栈探测"
  - "堆栈, 堆栈探测"
ms.assetid: 40daed7c-f942-4085-b872-01e12b37729e
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# /Gs（控制堆栈检查调用）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

控制堆栈探测。  
  
## 语法  
  
```  
/Gs[size]  
```  
  
## 参数  
 `size`  
 （可选）在启动堆栈探测之前局部变量可以占用的字节数。  如果在不指定 `size` 参数的情况下指定 **\/Gs** 选项，则这与指定 **\/Gs0** 的效果相同。  
  
## 备注  
 堆栈探测是编译器插入到每个函数调用中的代码序列。  堆栈探测启动时，它在内存中良性延伸存储函数的局部变量所需的空间量。  
  
 如果函数的局部变量需要的堆栈空间多于 `size` 字节，则启动它的堆栈探测。  默认情况下，当函数需要的堆栈空间多于一页时，编译器将生成启动堆栈探测的代码。  这等效于 x86 的 **\/Gs4096**、[!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 和 ARM 平台的编译器选项。  此值使应用程序和 Windows 内存管理器可以动态增加运行时提交给程序堆栈的内存量。  
  
> [!NOTE]
>  **\/Gs4096** 的默认值使 Windows 应用程序的程序堆栈可以在运行时适当增长。  我们建议，除非有确切的理由，否则请不要更改默认值。  
  
 某些程序（如虚拟设备驱动程序）并不需要这种默认堆栈增长机制。  在这些情况下，不需要堆栈探测，通过将 `size` 设置为大于任何函数（将需要局部变量存储）的值，可阻止编译器生成堆栈探测。  **\/Gs** 和 `size` 之间不允许有空格。  
  
 **\/Gs0** 为需要局部变量存储的每个函数调用激活堆栈探测。  这可对性能产生负面影响。  
  
 可以通过使用 [check\_stack](../../preprocessor/check-stack.md) 打开或关闭堆栈探测。  **\/Gs** 和 `check_stack` 杂注对标准 C 库例程没有影响；它们只影响你编译的函数。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  选择 **C\/C\+\+** 文件夹。  
  
3.  选择**“命令行”**属性页。  
  
4.  在**“附加选项”**框中键入编译器选项。  
  
### 以编程方式设置此编译器选项  
  
-   请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)