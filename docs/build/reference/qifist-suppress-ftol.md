---
title: "/QIfist（取消 _ftol） | Microsoft Docs"
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
  - "/qifist"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "QIfist 编译器选项 [C++]"
  - "-QIfist 编译器选项 [C++]"
  - "/QIfist 编译器选项 [C++]"
ms.assetid: 1afd32a5-f658-4b66-85f4-e0ce4cb955bd
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /QIfist（取消 _ftol）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当需要从浮点型转换为整型时，取消调用 Helper 函数 `_ftol`。  
  
## 语法  
  
```  
/QIfist  
```  
  
## 备注  
  
> [!NOTE]
>  **\/QIfist** 仅仅可用于面向 x86 的编译器中；此编译器选项不可用于面向 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 或ARM。  
  
 除了从浮点型转换为整型外，`_ftol` 函数还通过设置控制字的第 10 位和第 11 位来确保浮点单元 \(FPU\) 的舍入模式为向零方向（截断）。  这保证从浮点型转换为整型时的操作正如 ANSI C 标准所描述的一样（丢弃数字的小数部分）。  而使用 **\/QIfist** 时，不再保证获得此结果。  舍入模式应是记录在 Intel 参考手册中的四种模式之一：  
  
-   舍入为最接近的整数（若等距则为偶数）  
  
-   向负无穷大方向舍入  
  
-   向正无穷大方向舍入  
  
-   向零方向舍入  
  
 可以使用 [\_control87、\_controlfp、\_\_control87\_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) C 运行时函数修改 FPU 的舍入行为。  FPU 的默认舍入模式为“舍入为最接近的整数”。使用 **\/QIfist** 可以改善应用程序的性能，但并不是没有风险。  在生产环境中信任用 **\/QIfist** 生成的代码前，要彻底测试对舍入模式敏感的代码部分。  
  
 [\/arch \(x86\)](../../build/reference/arch-x86.md) 和 **\/QIfist** 不能在同一 compiland 上使用。  
  
> [!NOTE]
>  默认情况下，**\/QIfist** 是无效的，因为舍入位数也会影响浮点到浮点的舍入（在每次计算后发生），因此，当设置 C 样式（向零方向）舍入的标志时，浮点计算可能会不同。  如果代码取决于截断浮点数的小数部分的预期行为，则不应使用 **\/QIfist**。  如果没有把握，请不要使用 **\/QIfist**。  
  
 **\/QIfist** 已弃用。  编译器极大地提高了浮点到整数的转换速度。  有关详细信息，请参阅[Deprecated Compiler Options in Visual C\+\+ 2005](http://msdn.microsoft.com/zh-cn/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce)。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“命令行”**属性页。  
  
4.  在**“附加选项”**框中键入编译器选项。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [\/Q 选项（低级别操作）](../../build/reference/q-options-low-level-operations.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)