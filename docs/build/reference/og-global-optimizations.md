---
title: "/Og（全局优化） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.GlobalOptimizations"
  - "/og"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Og 编译器选项 [C++]"
  - "自动注册分配"
  - "通用子表达式消除"
  - "全局优化编译器选项 [C++]"
  - "循环结构, 优化"
  - "Og 编译器选项 [C++]"
  - "-Og 编译器选项 [C++]"
ms.assetid: d10630cc-b9cf-4e97-bde3-8d7ee79e9435
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# /Og（全局优化）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供局部优化和全局优化、自动寄存器分配和循环优化。  已否决。  
  
## 语法  
  
```  
/Og  
```  
  
## 备注  
 可使用下列优化：  
  
-   局部和全局公共子表达式消除  
  
     在此优化中，计算一次公共子表达式的值。  在下面的示例中，如果 `b` 和 `c` 的值在三个表达式之间没有更改，则编译器可以将 `b + c` 的计算结果分配给一个临时变量，用此变量替代 `b + c`：  
  
    ```  
    a = b + c;  
    d = b + c;  
    e = b + c;  
    ```  
  
     对于局部公共子表达式优化，编译器检查公共子表达式的一小部分代码。  对于全局公共子表达式优化，编译器搜索全部函数中的公共子表达式。  
  
-   自动寄存器分配  
  
     此优化允许编译器将常用变量和子表达式存储在寄存器中；忽略 `register` 关键字。  
  
-   循环优化  
  
     此优化将不变量子表达式从循环体中移除。  最佳循环只包含其值在每次循环执行过程中都要更改的表达式。  在下面的示例中，表达式 `x + y` 在循环体中不更改：  
  
    ```  
    i = -100;  
    while( i < 0 ) {  
        i += x + y;  
    }  
    ```  
  
     优化之后，计算一次 `x + y` 而不是每次执行循环时都计算：  
  
    ```  
    i = -100;  
    t = x + y;  
    while( i < 0 ) {  
        i += t;  
    }  
    ```  
  
     当编译器不能假定任何别名时（通过 [\_\_restrict](../../cpp/extension-restrict.md)、[noalias](../../cpp/noalias.md) 或 [restrict](../../cpp/restrict.md) 设置），循环优化更有效。  
  
    > [!NOTE]
    >  使用带 `g` 选项的 `optimize`  杂注，可以逐个函数地启用或禁用全局优化。  
  
 **\/Og** 还会启用命名的返回值优化，此优化可消除基于堆栈的返回值的复制构造函数和析构函数。  有关更多信息，请参见[\/O1、\/O2（最小化大小、最大化速度）](../../build/reference/o1-o2-minimize-size-maximize-speed.md)。  
  
 若要了解相关信息，请参见 [生成内部函数 \(\/Oi\)](../../build/reference/oi-generate-intrinsic-functions.md) 和 [完全优化 \(\/Ox\)](../../build/reference/ox-full-optimization.md)。  
  
 **\/Og** 已弃用；请使用 [\/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md) 或 **\/O2**。  有关详细信息，请参阅[Deprecated Compiler Options in Visual C\+\+ 2005](http://msdn.microsoft.com/zh-cn/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce)。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“命令行”**属性页。  
  
4.  在**“附加选项”**框中键入编译器选项。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [\/O 选项（优化代码）](../../build/reference/o-options-optimize-code.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)