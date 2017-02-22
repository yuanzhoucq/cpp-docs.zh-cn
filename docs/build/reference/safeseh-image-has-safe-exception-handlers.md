---
title: "/SAFESEH（图像具有安全异常处理程序） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/SAFESEH"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/SAFESEH 链接器选项"
  - "-SAFESEH 链接器选项"
  - "SAFESEH 链接器选项"
ms.assetid: 7722ff99-b833-4c65-a855-aaca902ffcb7
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# /SAFESEH（图像具有安全异常处理程序）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/SAFESEH[:NO]  
```  
  
 在指定 **\/SAFESEH** 后，只有在链接器还可以生成映像的安全异常处理程序表的情况下，该链接器才会生成一个映像。  此表为操作系统指定哪些异常处理程序对映像有效。  
  
 只有在对 x86 目标进行链接时，**\/SAFESEH** 才有效。  已注明异常处理程序的平台不支持 **\/SAFESEH**。  例如，在 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 和 ARM 上，所有异常处理程序都在 PDATA 中注明。  ML64.exe 支持添加批注，这些批注将 SEH 信息（XDATA 和 PDATA）发出到映像中，允许您通过 ml64 函数展开。  有关更多信息，请参见[MASM for x64 \(ml64.exe\)](../../assembler/masm/masm-for-x64-ml64-exe.md)。  
  
 如果未指定 **\/SAFESEH**，链接器将生成具有安全异常处理程序表的映像（如果所有模块都与安全异常处理功能兼容）。  如果任意模块与安全异常处理功能不兼容，则最终的映像将不会包含安全异常处理程序表。  如果 [\/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) 指定 WINDOWSCE 或某一 EFI\_\* 选项，则链接器将不尝试生成具有安全异常处理程序表的映像，因为上述任何子系统都不可以利用这些信息。  
  
 如果指定了 **\/SAFESEH:NO**，则链接器将不会生成具有安全异常处理程序表的映像，即使所有模块都与安全异常处理程序功能兼容。  
  
 链接器无法生成映像的最常见的原因是：该链接器的一个或多个输入文件（模块）与安全异常处理程序功能不兼容。  模块与安全异常处理程序不兼容的一个常见原因是：该模块是通过来自以前版本的 Visual C\+\+ 的编译器创建的。  
  
 通过使用 [.SAFESEH](../../assembler/masm/dot-safeseh.md)，还可以将函数注册为结构化的异常处理程序。  
  
 无法将现有的二进制文件标记为具有安全异常处理程序（或不具有异常处理程序）；必须在生成时添加关于安全异常处理的信息。  
  
 链接器能否生成安全异常处理程序表取决于使用 C 运行库的应用程序。  如果使用 [\/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) 进行链接，并希望得到一张安全异常处理程序表，则需要提供加载配置结构（例如可在 loadcfg.c CRT 源文件中找到的结构），此结构包含为 Visual C\+\+ 定义的所有项。  例如：  
  
```  
#include <windows.h>  
extern DWORD_PTR __security_cookie;  /* /GS security cookie */  
  
/*  
 * The following two names are automatically created by the linker for any  
 * image that has the safe exception table present.  
*/  
  
extern PVOID __safe_se_handler_table[]; /* base of safe handler entry table */  
extern BYTE  __safe_se_handler_count;  /* absolute symbol whose address is  
                                           the count of table entries */  
typedef struct {  
    DWORD       Size;  
    DWORD       TimeDateStamp;  
    WORD        MajorVersion;  
    WORD        MinorVersion;  
    DWORD       GlobalFlagsClear;  
    DWORD       GlobalFlagsSet;  
    DWORD       CriticalSectionDefaultTimeout;  
    DWORD       DeCommitFreeBlockThreshold;  
    DWORD       DeCommitTotalFreeThreshold;  
    DWORD       LockPrefixTable;            // VA  
    DWORD       MaximumAllocationSize;  
    DWORD       VirtualMemoryThreshold;  
    DWORD       ProcessHeapFlags;  
    DWORD       ProcessAffinityMask;  
    WORD        CSDVersion;  
    WORD        Reserved1;  
    DWORD       EditList;                   // VA  
    DWORD_PTR   *SecurityCookie;  
    PVOID       *SEHandlerTable;  
    DWORD       SEHandlerCount;  
} IMAGE_LOAD_CONFIG_DIRECTORY32_2;  
  
const IMAGE_LOAD_CONFIG_DIRECTORY32_2 _load_config_used = {  
    sizeof(IMAGE_LOAD_CONFIG_DIRECTORY32_2),  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    0,  
    &__security_cookie,  
    __safe_se_handler_table,  
    (DWORD)(DWORD_PTR) &__safe_se_handler_count  
};  
```  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择 **Linker** 文件夹。  
  
3.  选择**“命令行”**属性页。  
  
4.  将该选项键入**“附加选项”**框中。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)