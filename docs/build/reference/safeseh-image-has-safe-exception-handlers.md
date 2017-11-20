---
title: "-SAFESEH （图像具有安全异常处理程序） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /SAFESEH
dev_langs: C++
helpviewer_keywords:
- /SAFESEH linker option
- -SAFESEH linker option
- SAFESEH linker option
ms.assetid: 7722ff99-b833-4c65-a855-aaca902ffcb7
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 430991838245e258a8f1b4bffe16a2f559019901
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="safeseh-image-has-safe-exception-handlers"></a>/SAFESEH（图像具有安全异常处理程序）
```  
/SAFESEH[:NO]  
```  
  
 当**/SAFESEH**指定，是否它还可以生成的图像的安全异常处理程序表，链接器才将生成一个映像。 此表指定哪些异常处理程序是适合于该映像的操作系统。  
  
 **/SAFESEH**针对 x86 链接时才有效目标。 **/SAFESEH**已记下的异常处理程序的平台不支持。 例如，在 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 和 ARM 上，所有异常处理程序都在 PDATA 中注明。 ML64.exe 到的映像，并可通过 ml64 函数展开具有用于添加批注发出 SEH 信息 （XDATA 和 PDATA） 支持。 请参阅[x64 (ml64.exe) 的 MASM](../../assembler/masm/masm-for-x64-ml64-exe.md)有关详细信息。  
  
 如果**/SAFESEH**未指定，则链接器将生成具有安全异常处理程序表的图像，如果所有模块都都与安全异常处理功能兼容。 如果任何模块不兼容与安全异常处理功能，则生成的映像将不包含安全异常处理程序表。 如果[/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) WINDOWSCE 或 EFI_ * 选项之一，指定链接器不会尝试生成具有安全异常处理程序表映像都不这些子系统可以进行信息的使用。  
  
 如果**/SAFESEH:NO**指定，则链接器将不会生成安全异常处理程序表的映像，即使所有模块都都与安全异常处理功能兼容。  
  
 链接器不要无法生成映像的最常见原因是因为一个或多个到链接器输入文件 （模块） 未与安全异常处理程序功能兼容。 要与安全异常处理程序不兼容的模块的常见原因是因为它创建使用从以前版本的 Visual c + + 编译器。  
  
 你还可以将函数通过注册为结构化的异常处理程序[。SAFESEH](../../assembler/masm/dot-safeseh.md)。  
  
 不能将标记的现有二进制为具有安全异常处理程序 （或没有异常处理程序）;必须在生成时添加安全异常处理的信息。  
  
 链接器的功能将生成安全异常处理程序表依赖于使用 C 运行库的应用程序。 如果与链接[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)并且想要安全异常处理程序表，则需要提供负载配置结构 （如，可以在 loadcfg.c CRT 源文件中找到），它包含为 Visual c + + 定义的所有项。 例如:   
  
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
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择**链接器**文件夹。  
  
3.  选择**命令行**属性页。  
  
4.  该选项输入**其他选项**框。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
-   请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>另请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)