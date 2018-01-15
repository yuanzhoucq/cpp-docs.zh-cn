---
title: "-SUBSYSTEM （指定子系统） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /subsystem
- VC.Project.VCLinkerTool.SubSystem
- VC.Project.VCLinkerTool.SubSystemVersion
dev_langs: C++
helpviewer_keywords:
- /SUBSYSTEM linker option
- SUBSYSTEM linker option
- -SUBSYSTEM linker option
- subsystem specifications
ms.assetid: d7b133cf-cf22-4da8-ab46-6552702c0b9b
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3fd96a89ef4228835307f8f8f0d9fff5d61441f9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="subsystem-specify-subsystem"></a>/SUBSYSTEM（指定子系统）
```  
/SUBSYSTEM:{BOOT_APPLICATION|CONSOLE|EFI_APPLICATION|  
            EFI_BOOT_SERVICE_DRIVER|EFI_ROM|EFI_RUNTIME_DRIVER|NATIVE|  
            POSIX|WINDOWS)  
            [,major[.minor]]  
```  
  
 BOOT_APPLICATION  
 在 Windows 启动环境中运行的应用程序。 有关启动应用程序的详细信息，请参阅[关于 BCD](http://msdn.microsoft.com/library/windows/desktop/aa362639)。  
  
 CONSOLE  
 Win32 字符模式应用程序。 操作系统提供为控制台应用程序提供控制台。 如果`main`或`wmain`为本机代码中，定义`int main(array<String ^> ^)`定义对于托管代码，或你生成应用程序完全使用`/clr:safe`，控制台是默认设置。  
  
 可扩展固件接口  
 EFI_ * 子系统。 请参阅 EFI 规范的详细信息。 有关示例，请参阅 Intel 网站。 最小和默认版本为 1.0。  
  
 NATIVE  
 Windows NT 的内核模式驱动程序。 此选项通常为 Windows 系统组件保留。 如果[/DRIVER:WDM](../../build/reference/driver-windows-nt-kernel-mode-driver.md)指定，则本机是默认设置。  
  
 POSIX  
 使用 Windows NT 中的 POSIX 子系统运行的应用程序。  
  
 窗口  
 应用程序不需要控制台中，因为它可以创建其自己的与用户交互的窗口。 如果`WinMain`或`wWinMain`定义对于本机代码，或`WinMain(HISTANCE *, HINSTANCE *, char *, int)`或`wWinMain(HINSTANCE *, HINSTANCE *, wchar_t *, int)`定义托管代码中，对于 WINDOWS 是默认值。  
  
 `Major`和`minor`（可选）  
 指定的子系统的最低所需的版本。 这些参数是十进制数字 0 到 65535 范围内。 请参阅有关详细信息备注。 为版本号没有上限。  
  
## <a name="remarks"></a>备注  
 /SUBSYSTEM 选项指定的可执行文件的环境。  
  
 子系统的选择会影响的入口点符号 （或入口点函数） 链接器将选择。  
  
 可选的最小值和默认`major`和`minor`的子系统版本号包括，如下所示。  
  
|子系统|最低|默认|  
|---------------|-------------|-------------|  
|BOOT_APPLICATION|1.0|1.0|  
|CONSOLE|(x86) 5.01 5.02 ([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]) 6.02 (ARM)|6.00 (x86、 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]) 6.02 (ARM)|  
|窗口|(x86) 5.01 5.02 ([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]) 6.02 (ARM)|6.00 (x86、 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]) 6.02 (ARM)|  
|本机 （带驱动程序： WDM)|(x86) 1.00 1.10 ([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]，ARM)|(x86) 1.00 1.10 ([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]，ARM)|  
|本机 （不带 /DRIVER:WDM)|(x86) 4.00 5.02 ([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]) 6.02 (ARM)|(x86) 4.00 5.02 ([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]) 6.02 (ARM)|  
|POSIX|1.0|19.90|  
|EFI_APPLICATION，EFI_BOOT_SERVICE_DRIVER，EFI_ROM EFI_RUNTIME_DRIVER|1.0|1.0|  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择链接器文件夹。  
  
3.  选择**系统**属性页。  
  
4.  修改`SubSystem`属性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SubSystem%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)