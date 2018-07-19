---
title: -GS （缓冲区安全检查） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.BufferSecurityCheck
- VC.Project.VCCLCompilerTool.BufferSecurityCheck
- /GS
dev_langs:
- C++
helpviewer_keywords:
- buffers [C++], buffer overruns
- buffer overruns, compiler /GS switch
- GS compiler option [C++]
- /GS compiler option [C++]
- security check compiler option [C++]
- -GS compiler option [C++]
- buffers [C++], avoiding overruns
ms.assetid: 8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6aa1204a6959121b3f6280433c0414f81c038548
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379479"
---
# <a name="gs-buffer-security-check"></a>/GS（缓冲区安全检查）  
  
检测到某些覆盖函数的返回地址、 异常处理程序地址或某些类型的参数的缓冲区溢出。 导致缓冲区溢出是黑客用于利用不会强制缓冲区大小限制的代码的方法。  
  
## <a name="syntax"></a>语法  
  
```  
/GS[-]  
```  
  
## <a name="remarks"></a>备注  
  
**/GS**默认是打开的。 如果您希望应用程序拥有不出现安全漏洞，使用 **/GS-**。 有关详细信息 **/GS**，请参阅[编译器安全检查在深度](http://go.microsoft.com/fwlink/p/?linkid=7260)。 有关禁止缓冲区溢出检测的详细信息，请参阅[safebuffers](../../cpp/safebuffers.md)。  
  
## <a name="security-checks"></a>安全检查  
  
编译器认为容易缓冲区溢出问题的函数，编译器分配的返回地址之前堆栈上的空间。 在进入函数时，分配的空间加载与*安全 cookie* ，会在模块加载一次计算。 在函数退出时，并在 64 位操作系统上的帧展开过程，调用帮助器函数若要确保的 cookie 的值仍为相同。 不同的值指示堆栈的覆盖可能已发生。 如果检测到一个不同的值，则进程将终止。  
  
## <a name="gs-buffers"></a>GS 缓冲区  
  
在执行缓冲区溢出安全检查*GS 缓冲区*。 GS 缓冲区可以是以下方法之一：  
  
-   数组是大于 4 个字节，超过两个元素，并具有不是指针类型的元素类型。  
  
-   一种数据结构，其大小超过 8 个字节且不包含指针。  
  
-   通过使用分配的缓冲区[_alloca](../../c-runtime-library/reference/alloca.md)函数。  
  
-   任何类或结构，其中包含 GS 缓冲区。  
  
例如，以下语句声明 GS 缓冲区。  
  
```cpp  
char buffer[20];  
int buffer[20];  
struct { int a; int b; int c; int d; } myStruct;  
struct { int a; char buf[20]; };  
```  
  
但是，以下语句不声明 GS 缓冲区。 前两个声明包含的指针类型的元素。 第三个和第四个语句声明其大小来说太小的数组。 第五个语句声明一个结构，其大小在 x86 平台不是超过 8 个字节。  
  
```cpp  
char *pBuf[20];  
void *pv[20];  
char buf[4];  
int buf[2];  
struct { int a; int b; };  
```  
  
## <a name="initialize-the-security-cookie"></a>初始化安全 Cookie  
  
**/GS**编译器选项需要运行使用 cookie 的任何函数之前，初始化安全 cookie。 在进入 EXE 或 DLL，必须立即初始化安全 cookie。 如果你使用默认 VCRuntime 入口点自动完成： mainCRTStartup，wmainCRTStartup，WinMainCRTStartup，wWinMainCRTStartup，或 _DllMainCRTStartup。 如果你使用的备用入口点，必须通过调用手动初始化安全 cookie [__security_init_cookie](../../c-runtime-library/reference/security-init-cookie.md)。  
  
## <a name="what-is-protected"></a>保护的内容  
  
**/GS**编译器选项保护以下各项：  
  
-   函数调用的寄信人地址。  
  
-   异常处理程序函数的地址。  
  
-   易受攻击的函数参数。  
  
在所有平台上 **/GS**尝试检测到的寄信人地址的缓冲区溢出。 缓冲区溢出可以更容易地利用平台例如 x86 和 x64，使用函数调用的返回地址存储在堆栈的调用约定。  
  
在 x86，如果函数使用异常处理程序，编译器将插入一个安全 cookie 以保护异常处理程序的地址。 在帧展开过程将先检查 cookie。  
  
**/GS**保护*易受攻击参数*传递到函数。 易受攻击的参数是指针，c + + 参考，C-包含的结构 （c + + POD 类型） 的指针或 GS 缓冲区。  
  
易受攻击参数分配之前的 cookie 和本地变量中。 缓冲区溢出可以覆盖这些参数。 和之前该函数将返回并执行安全检查，使用这些参数的函数中的代码会导致攻击。 为了尽量减少这种危险，编译器将函数 prolog 期间生成的易受攻击的参数的副本，并将其置于存储区域的所有缓冲区下方。  
  
编译器不在的以下情况下进行易受攻击的参数的副本：  
  
-   不包含 GS 缓冲区的函数。  
  
-   优化 ([/O 选项](../../build/reference/o-options-optimize-code.md)) 未启用。  
  
-   具有变量自变量列表 （...） 的函数。  
  
-   函数标记有[裸](../../cpp/naked-cpp.md)。  
  
-   包含内联程序集代码中的第一个语句的函数。  
  
-   仅以不太可能被利用发生缓冲区溢出的方式使用一个参数。  
  
## <a name="what-is-not-protected"></a>哪些不受保护  
  
**/GS**编译器选项不能防止所有的缓冲区溢出安全攻击。 例如，如果你有缓冲区和 vtable 对象中，缓冲区溢出可能会损坏 vtable。  
  
即使你使用 **/GS**，始终尝试编写没有缓冲区溢出的安全代码。  
  
### <a name="to-set-this-compiler-option-in-visual-studio"></a>在 Visual Studio 中设置此编译器选项  
  
1.  在**解决方案资源管理器**，右键单击项目，然后单击**属性**。  
  
     有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  在**属性页**对话框中，单击**C/c + +** 文件夹。  
  
3.  单击**代码生成**属性页。  
  
4.  修改**缓冲区安全检查**属性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BufferSecurityCheck%2A>。  
  
## <a name="example"></a>示例  
  
此示例会发生缓冲区溢出。 这将导致应用程序在运行时失败。  
  
```C  
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
  
## <a name="see-also"></a>请参阅  
  
[编译器选项](../../build/reference/compiler-options.md)   
[设置编译器选项](../../build/reference/setting-compiler-options.md)