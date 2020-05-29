---
title: /GS（缓冲区安全检查）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.BufferSecurityCheck
- VC.Project.VCCLCompilerTool.BufferSecurityCheck
helpviewer_keywords:
- buffers [C++], buffer overruns
- buffer overruns, compiler /GS switch
- GS compiler option [C++]
- /GS compiler option [C++]
- security check compiler option [C++]
- -GS compiler option [C++]
- buffers [C++], avoiding overruns
ms.assetid: 8d8a5ea1-cd5e-42e1-bc36-66e1cd7e731e
ms.openlocfilehash: 92d296e8079a9ecd8d366c46bbdad8b2ee5dc313
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439560"
---
# <a name="gs-buffer-security-check"></a>/GS（缓冲区安全检查）

检测某些覆盖函数的返回地址、异常处理程序地址或某些类型的参数的缓冲区溢出。 导致缓冲区溢出是黑客用来利用不强制缓冲区大小限制的代码的一种技术。

## <a name="syntax"></a>语法

```
/GS[-]
```

## <a name="remarks"></a>备注

默认情况下， **/gs**处于启用状态。 如果你希望你的应用程序不存在安全漏洞，请使用 **/GS-** 。 有关抑制缓冲区溢出检测的详细信息，请参阅[safebuffers](../../cpp/safebuffers.md)。

## <a name="security-checks"></a>安全检查

在编译器识别为受缓冲区溢出问题的函数时，编译器会在返回地址之前在堆栈上分配空间。 在函数项上，使用在模块加载时计算的*安全 cookie*加载分配的空间。 在函数退出时，以及在64位操作系统的帧展开期间，将调用 helper 函数以确保 cookie 的值仍然相同。 其他值表示可能发生了堆栈覆盖。 如果检测到其他值，将终止该进程。

## <a name="gs-buffers"></a>GS 缓冲区

对*GS 缓冲区*执行缓冲区溢出安全检查。 GS 缓冲区可以是以下项之一：

- 大于4个字节的数组，包含两个以上的元素，并且其元素类型不是指针类型。

- 大小超过8个字节且不包含任何指针的数据结构。

- 使用[_alloca](../../c-runtime-library/reference/alloca.md)函数分配的缓冲区。

- 包含 GS 缓冲区的任何类或结构。

例如，下面的语句声明 GS 缓冲区。

```cpp
char buffer[20];
int buffer[20];
struct { int a; int b; int c; int d; } myStruct;
struct { int a; char buf[20]; };
```

但是，以下语句不会声明 GS 缓冲区。 前两个声明包含指针类型的元素。 第三个和第四个语句声明的数组的大小太小。 第五个语句声明一个结构，其在 x86 平台上的大小不超过8个字节。

```cpp
char *pBuf[20];
void *pv[20];
char buf[4];
int buf[2];
struct { int a; int b; };
```

## <a name="initialize-the-security-cookie"></a>初始化安全 Cookie

**/Gs**编译器选项要求在运行任何使用 cookie 的函数之前初始化安全 cookie。 安全 cookie 必须立即初始化为 EXE 或 DLL。 如果使用默认的 VCRuntime 入口点： mainCRTStartup、wmainCRTStartup、WinMainCRTStartup、wWinMainCRTStartup 或 _DllMainCRTStartup，则会自动执行此操作。 如果使用备用入口点，则必须通过调用[__security_init_cookie](../../c-runtime-library/reference/security-init-cookie.md)来手动初始化安全 cookie。

## <a name="what-is-protected"></a>受保护的内容

**/Gs**编译器选项保护以下项：

- 函数调用的返回地址。

- 函数的异常处理程序的地址。

- 易受攻击的函数参数。

在所有平台上， **/gs**都尝试检测返回地址中的缓冲区溢出。 在 x86 和 x64 等平台上，可以更容易地利用缓冲区溢出，它们使用调用约定将函数调用的返回地址存储在堆栈上。

在 x86 上，如果函数使用异常处理程序，则编译器将插入一个安全 cookie 来保护异常处理程序的地址。 帧展开期间会检查 cookie。

**/Gs**保护传递到函数中的*易受攻击的参数*。 易受攻击的参数是一种C++指针、引用、包含指针的C++ C 结构（POD 类型）或 GS 缓冲区。

在 cookie 变量和局部变量之前，将分配一个有漏洞的参数。 缓冲区溢出可以覆盖这些参数。 在函数返回之前，使用这些参数的函数中的代码可能会导致攻击，并执行安全检查。 为了最大限度地降低这种风险，编译器会在函数 prolog 期间复制易受攻击的参数，并将其放在所有缓冲区的存储区域下方。

在以下情况下，编译器不会生成易受攻击的参数的副本：

- 不包含 GS 缓冲区的函数。

- 不启用优化（[/o 选项](o-options-optimize-code.md)）。

- 具有变量参数列表（...）的函数。

- 用[naked](../../cpp/naked-cpp.md)标记的函数。

- 在第一个语句中包含内联程序集代码的函数。

- 参数的使用方法仅在于在出现缓冲区溢出时可能会被利用的方式。

## <a name="what-is-not-protected"></a>不受保护的内容

**/Gs**编译器选项不能防止所有缓冲区溢出安全攻击。 例如，如果对象中有一个缓冲区和一个 vtable，缓冲区溢出可能会损坏 vtable。

即使使用的是 **/gs**，也应始终尝试编写没有缓冲区溢出的安全代码。

### <a name="to-set-this-compiler-option-in-visual-studio"></a>在 Visual Studio 中设置此编译器选项

1. 在**解决方案资源管理器**中，右键单击项目，然后单击 "**属性**"。

   有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 在 "**属性页**" 对话框中，单击 " **CC++ /** 文件夹"。

1. 单击 "**代码生成**" 属性页。

1. 修改 "**缓冲区安全检查**" 属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BufferSecurityCheck%2A>。

## <a name="example"></a>示例

此示例溢出缓冲区。 这会导致应用程序在运行时失败。

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

## <a name="see-also"></a>另请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
