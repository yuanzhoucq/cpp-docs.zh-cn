---
title: "/GT（支持纤程安全的线程本地存储区） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.EnableFiberSafeOptimizations"
  - "/gt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/GT 编译器选项 [C++]"
  - "纤维安全静态线程本地存储区编译器选项 [C++]"
  - "GT 编译器选项 [C++]"
  - "-GT 编译器选项 [C++]"
  - "静态线程-本地存储区和纤维安全"
  - "线程本地存储区"
ms.assetid: 071fec79-c701-432b-9970-457344133159
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /GT（支持纤程安全的线程本地存储区）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

支持使用静态线程本地存储区分配的数据（即用 `__declspec(thread)` 分配的数据）的纤程安全。  
  
## 语法  
  
```  
/GT  
```  
  
## 备注  
 通过线程本地存储区 \(TLS\) 数组引用用 `__declspec(thread)` 声明的数据。  TLS 数组是系统为每个线程维护的地址数组。  此数组中的每个地址提供线程本地存储区数据的位置。  
  
 纤程是轻量对象，由堆栈和寄存器上下文组成，并可安排在各种线程上。  纤程可以在任意线程上运行。  因为纤程可能会交换出去并且稍后在不同的线程上重新启动，所以 TLS 数组的地址不得缓存或优化为函数调用中的公共子表达式（有关详细信息，请参见 [\/Og（全局优化）](../../build/reference/og-global-optimizations.md) 选项）。  **\/GT** 阻止此类优化。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“优化”**属性页。  
  
4.  修改**“启用纤程安全优化”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFiberSafeOptimizations%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)