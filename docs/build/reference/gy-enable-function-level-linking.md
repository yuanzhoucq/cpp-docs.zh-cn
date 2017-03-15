---
title: "/Gy（启用函数级链接） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.EnableFunctionLevelLinking"
  - "/gy"
  - "VC.Project.VCCLWCECompilerTool.EnableFunctionLevelLinking"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Gy 编译器选项 [C++]"
  - "COMDAT 函数"
  - "启用函数级链接编译器选项 [C++]"
  - "Gy 编译器选项 [C++]"
  - "-Gy 编译器选项 [C++]"
  - "封装函数"
ms.assetid: 0d3cf14c-ed7d-4ad3-b4b6-104e56f61046
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# /Gy（启用函数级链接）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

允许编译器以打包函数\(COMDATs\)的形式对各个函数进行打包。  
  
## 语法  
  
```  
/Gy[-]  
```  
  
## 备注  
 链接器要求单独打包为 COMDAT 的函数在 DLL 或 .exe 文件中排除或安排各个函数。  
  
 可以使用链接器选项 [\/OPT（优化）](../../build/reference/opt-optimizations.md) 从 .exe 文件中排除未引用的封装函数。  
  
 可以使用链接器选项 [\/ORDER（按顺序放置函数）](../../build/reference/order-put-functions-in-order.md)按指定顺序将封装函数包括在 .exe 文件中。  
  
 如果内联函数作为调用进行实例化（例如，当关闭内联或获取函数地址时出现这种情况），则始终打包内联函数。  另外，在类声明内部定义的 C\+\+ 成员函数会自动打包；其他函数不会如此，所以需要选择此选项以便将它们作为封装函数编译。  
  
> [!NOTE]
>  用于“编辑并继续”的 [\/ZI](../../build/reference/z7-zi-zi-debug-information-format.md) 选项会自动设置 **\/Gy** 选项。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“代码生成”**属性页。  
  
4.  修改**“启用函数级链接”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFunctionLevelLinking%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)