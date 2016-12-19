---
title: "/O1、/O2（最小化大小、最大化速度） | Microsoft Docs"
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
  - "/o2"
  - "/o1"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/O1 编译器选项 [C++]"
  - "/O2 编译器选项 [C++]"
  - "快速代码"
  - "最大化速度编译器选项 [C++]"
  - "最小化大小编译器选项 [C++]"
  - "O1 编译器选项 [C++]"
  - "-O1 编译器选项 [C++]"
  - "O2 编译器选项 [C++]"
  - "-O2 编译器选项 [C++]"
  - "小型代码"
ms.assetid: 2d1423f5-53d9-44da-8908-b33a351656c2
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /O1、/O2（最小化大小、最大化速度）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

选择一组影响文件大小和速度的预定义选项。  
  
## 语法  
  
```  
/O1  
/O2  
```  
  
## 备注  
 下表介绍 **\/O1** 和 **\/O2**。  
  
|选项|等效于|注释|  
|--------|---------|--------|  
|**\/O1**（最小化大小）|**\/Og \/Os \/Oy \/Ob2 \/Gs \/GF \/Gy**|在多数情况下创建最小的代码。|  
|**\/O2**（最大化速度）|**\/Og \/Oi \/Ot \/Oy \/Ob2 \/Gs \/GF \/Gy**|在大多数情况下，创建运行速度最快的代码。（发布版本的默认设置）|  
  
 **\/O1** 和 **\/O2** 也支持命名返回值优化，它消除了基于堆栈的返回值的复制构造函数和析构函数。  请看下面的示例。`Test` 函数将不创建复制构造函数或析构函数。  将输出语句添加到构造函数、析构函数和复制构造函数，以查看在运行程序时命名返回值优化的效果。  有关更多信息，请参见 [在 Visual C\+\+ 2005 中为的返回值优化](http://go.microsoft.com/fwlink/?linkid=131571)。  
  
```  
// O1_O2_NRVO.cpp  
// compile with: /O1  
struct A {  
   A() {}  
   ~A() {}  
   A(const A& aa) {}  
};  
  
A Test() {  
   A a;  
   return a;  
}  
int main() {  
   A aa;  
   aa = Test();  
}  
```  
  
 **x86 专用**  
  
 这些选项隐含使用“框架指针省略”\([\/Oy](../../build/reference/oy-frame-pointer-omission.md)\) 选项。  
  
 **END x86 Specific**  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“优化”**属性页。  
  
4.  修改**“优化”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>。  
  
## 请参阅  
 [\/O 选项（优化代码）](../../build/reference/o-options-optimize-code.md)   
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [\/EH（异常处理模型）](../../build/reference/eh-exception-handling-model.md)