---
title: "/sdl（启用附加安全检查） | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.SDLCheck"
dev_langs: 
  - "C++"
ms.assetid: 3dcf86a0-3169-4240-9f29-e04a9f535826
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /sdl（启用附加安全检查）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

添加建议的安全开发生命周期 \(SDL\) 检查。  这些检查包括额外的被视为错误的安全相关警告以及其他安全代码生成功能。  
  
## 语法  
  
```  
/sdl[-]  
```  
  
## 备注  
 **\/sdl** 启用 [\/GS](../../build/reference/gs-buffer-security-check.md) 提供的基线安全检查的超集并重写 **\/GS\-**。  默认情况下，**\/sdl** 处于关闭状态。  **\/sdl\-** 禁用额外的安全检查。  
  
## 编译时检查  
 **\/sdl** 启用以下被视为错误的警告：  
  
|\/sdl 启用的警告|等效的命令行开关|说明|  
|-----------------|--------------|--------|  
|[C4146](../../error-messages/compiler-warnings/compiler-warning-level-2-c4146.md)|\/we4146|将一元减号运算符应用于无符号类型，并生成了无符号的结果。|  
|[C4308](../../error-messages/compiler-warnings/compiler-warning-level-2-c4308.md)|\/we4308|将负整型常数转换为无符号类型，并生成了可能无意义的结果。|  
|[C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|\/we4532|在 `continue`\/`break` 块中使用 `goto`、`__finally` 或 `finally` 已在异常终止期间取消定义了行为。|  
|[C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|\/we4533|初始化变量的代码不会执行。|  
|[C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|\/we4700|使用未初始化的局部变量。|  
|[C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|\/we4703|使用可能未初始化的局部指针变量。|  
|[C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|\/we4789|使用特定 C 运行时 \(CRT\) 函数时缓冲区溢出。|  
|[C4995](../../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)|\/we4995|使用标记有杂注 [deprecated](../../preprocessor/deprecated-c-cpp.md) 的函数。|  
|[C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)|\/we4996|使用标记有 [deprecated](../../cpp/deprecated-cpp.md) 的函数。|  
  
## 运行时检查  
 启用 **\/sdl** 后，编译器将生成在运行时执行这些检查的代码：  
  
-   启用 **\/GS** 运行时缓冲区溢出检测的严格模式，等同于使用 `#pragma strict_gs_check(push, on)` 进行编译。  
  
-   执行有限的指针清理。  在不涉及取消引用的表达式中以及没有用户定义的析构函数的类型中，在调用 `delete` 后，指针引用将设置为无效的地址。  这有助于防止重复使用已过时的指针引用。  
  
-   执行类成员初始化。  在对象实例化时自动将所有类成员初始化为零（在构造函数运行前）。  这有助于防止使用与构造函数未显式初始化的类成员关联的未初始化的数据。  
  
## 备注  
 有关详细信息，请参阅[警告、\/sdl 和改进未初始化的变量检测](http://go.microsoft.com/fwlink/p/?LinkId=331012)。  
  
#### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参阅[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  选择 **C\/C\+\+** 文件夹。  
  
3.  在**“常规”**页上，从**“SDL 检查”**下拉列表中选择选项。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)