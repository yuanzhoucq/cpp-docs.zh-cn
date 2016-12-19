---
title: "/GS（缓冲区安全检查） | Microsoft Docs"
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
  - "VC.Project.VCCLWCECompilerTool.BufferSecurityCheck"
  - "VC.Project.VCCLCompilerTool.BufferSecurityCheck"
  - "/GS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "缓冲区 [C++], 缓冲区溢出"
  - "缓冲区溢出, 编译器 /GS 开关"
  - "GS 编译器选项 [C++]"
  - "/GS 编译器选项 [C++]"
  - "安全检查编译器选项 [C++]"
  - "-GS 编译器选项 [C++]"
  - "缓冲区 [C++], 避免溢出"
ms.assetid: 8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e
caps.latest.revision: 40
caps.handback.revision: 40
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /GS（缓冲区安全检查）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检测某些覆盖函数返回地址、异常处理程序地址或特定类型的参数的缓冲区溢出。  导致缓冲区溢出是黑客用于利用不强制缓冲区大小限制的代码的一种技术。  
  
## 语法  
  
```  
/GS[-]  
```  
  
## 备注  
 默认情况下，**\/GS** 处于打开状态。  如果希望应用程序不出现安全漏洞，请使用 **\/GS\-**。  有关 **\/GS** 的更多信息，请参见[编译器安全的深度制约](http://go.microsoft.com/fwlink/?linkid=7260)。  有关禁止缓冲区溢出检测的更多信息，请参见 [safebuffers](../../cpp/safebuffers.md)。  
  
## 安全检查  
 对于编译器认为容易出现缓冲区溢出问题的函数，编译器将在堆栈上返回地址之前分配空间。  在进入函数时，用安全 Cookie（它在模块加载时计算一次）加载分配的空间。  在退出函数时，以及在 64 位操作系统上展开帧的过程中，将调用 helper 函数，以确保 Cookie 值仍保持不变。  不同的值指示可能已覆盖堆栈。  如果检测到不同的值，则终止该进程。  
  
## GS 缓冲区  
 对 GS 缓冲区执行的缓冲区溢出安全检查。  GS 缓冲区可以是下列之一：  
  
-   一个大于 4 个字节的数组，它有两个以上的元素和一个并不是指针类型的元素类型。  
  
-   大小大于 8 字节且不包含指针的数据结构。  
  
-   通过使用 [\_alloca](../../c-runtime-library/reference/alloca.md) 函数分配的缓冲区。  
  
-   包含 GS 缓冲区的任何类或结构。  
  
 例如，下列语句声明 GS 缓冲区。  
  
```  
char buffer[20];  
int buffer[20];  
struct { int a; int b; int c; int d; } myStruct;  
struct { int a; char buf[20]; };  
```  
  
 但是，下列语句不会声明 GS 缓冲区。  前两个声明包含指针类型的元素。  第三个和第四个语句声明的数组太小。  第五个语句声明一个结构，此结构在 x86 平台上的大小不超过 8 个字节。  
  
```  
char *pBuf[20];  
void *pv[20];  
char buf[4];  
int buf[2];  
struct { int a; int b; };  
```  
  
## 初始化安全 Cookie  
 **\/GS** 编译器选项要求安全 cookie 在任何使用该 cookie 的函数运行前进行初始化。  在进入 EXE 或 DLL 时，安全 Cookie 必须进行初始化。  如果您使用默认 CRT 入口点（mainCRTStartup、wmainCRTStartup、WinMainCRTStartup、wWinMainCRTStartup 或 \_DllMainCRTStartup），这将自动完成。  如果使用的是备用入口点，则您必须通过调用 [\_\_security\_init\_cookie](../../c-runtime-library/reference/security-init-cookie.md) 手动初始化安全 cookie。  
  
## 哪些信息受保护  
 **\/GS** 编译器选项保护下列项。  
  
-   函数调用的返回地址。  
  
-   用于函数的异常处理程序的地址。  
  
-   易受攻击的函数参数。  
  
 在所有平台上，**\/GS** 尝试检测进入返回地址的缓冲区溢出。  通过调用约定将函数调用的返回地址存储到堆栈上，可以更容易地在平台（如 x86 和 x64）上利用缓冲区溢出。  
  
 在 x86 上，如果函数使用异常处理程序，则编译器将插入一个安全 Cookie 以保护异常处理程序的地址。  在展开帧的过程中会检查该 Cookie。  
  
 **\/GS** 可以防止向函数传入易受攻击的参数。  易受攻击的参数可以是一个指针、C\+\+ 引用、包含指针或 GS 缓冲区的 C 结构（C\+\+ POD 类型）。  
  
 易受攻击的参数在 Cookie 和局部变量之前分配。  缓冲区溢出可以覆盖这些参数。  并且，使用这些参数的函数中的代码可能在函数返回前就导致攻击并执行了安全检查。  若要尽量降低这种危险，编译器需要在函数 prolog 期间复制易受攻击的参数，并将它们置于所有缓冲区存储区域的下方。  
  
 在以下情况中，编译器不会制作易受攻击的参数的副本。  
  
-   函数不包含 GS 缓冲区。  
  
-   未启用优化 \([\/O 选项](../../build/reference/o-options-optimize-code.md)\)。  
  
-   具有可变参数列表的函数 \(...\)。  
  
-   标记有[裸](../../cpp/naked-cpp.md)的函数。  
  
-   函数的第一行语句包含内联程序集代码。  
  
-   仅通过在缓冲区溢出事件中不太可能利用的方式使用参数。  
  
## 哪些信息不受保护  
 **\/GS** 编译器选项不能抵御所有缓冲区溢出安全攻击。  例如，如果对象中有缓冲区和 vtable，则缓冲区溢出可能损坏该 vtable。  
  
 即使您使用 **\/GS**，也请始终尝试编写没有缓冲区溢出的安全代码。  
  
#### 在 Visual Studio 中设置此编译器选项  
  
1.  在**“解决方案资源管理器”**中右击该项目，再单击**“属性”**。  
  
     有关详细信息，请参阅[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  在**“属性页”**对话框中，单击**“C\/C\+\+”**文件夹。  
  
3.  单击**“代码生成”**属性页。  
  
4.  修改**“缓冲区安全检查”**属性。  
  
#### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BufferSecurityCheck%2A>。  
  
## 示例  
 此示例溢出缓冲区。  这样会使应用程序在运行时失败。  
  
```  
// compile with: /c /W1  
#include <cstring>  
#include <stdlib.h>  
#pragma warning(disable : 4996)   // for strcpy use  
  
// Vulnerable function  
void vulnerable(const char *str) {  
   char buffer[10];  
   strcpy(buffer, str); // overrun buffer !!!  
  
   // use a secure CRT function to help prevent buffer overruns  
   // truncate string to fit a 10 byte buffer  
   // strncpy_s(buffer, _countof(buffer), str, _TRUNCATE);  
}  
  
int main() {  
   // declare buffer that is bigger than expected  
   char large_buffer[] = "This string is longer than 10 characters!!";  
   vulnerable(large_buffer);  
}  
```  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)