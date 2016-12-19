---
title: "/SUBSYSTEM（指定子系统） | Microsoft Docs"
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
  - "/subsystem"
  - "VC.Project.VCLinkerTool.SubSystem"
  - "VC.Project.VCLinkerTool.SubSystemVersion"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/SUBSYSTEM 链接器选项"
  - "SUBSYSTEM 链接器选项"
  - "-SUBSYSTEM 链接器选项"
  - "子系统规范"
ms.assetid: d7b133cf-cf22-4da8-ab46-6552702c0b9b
caps.latest.revision: 25
caps.handback.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /SUBSYSTEM（指定子系统）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/SUBSYSTEM:{BOOT_APPLICATION|CONSOLE|EFI_APPLICATION|  
            EFI_BOOT_SERVICE_DRIVER|EFI_ROM|EFI_RUNTIME_DRIVER|NATIVE|  
            POSIX|WINDOWS)  
            [,major[.minor]]  
```  
  
 BOOT\_APPLICATION  
 运行 Windows 启动环境的应用程序。  有关启动应用程序的更多信息，请参见[关于 BCD](http://msdn.microsoft.com/library/windows/desktop/aa362639)。  
  
 CONSOLE  
 Win32 字符模式应用程序。  操作系统为各种控制台应用程序提供控制台。  如果为本机代码定义了 `main` 或 `wmain`，为托管代码定义了 `int main(array<String ^> ^)`，或者完全使用 `/clr:safe` 构建应用程序，则 CONSOLE 是默认值。  
  
 可扩展固件接口  
 EFI\_\* 子系统。  有关更多信息，请参见 EFI 规范。  例如，请参见 Intel 网站。  最低和默认版本都是 1.0。  
  
 NATIVE  
 Windows NT 内核模式驱动程序。  此选项通常是为 Windows 系统组件保留的。  如果指定 [\/DRIVER:WDM](../../build/reference/driver-windows-nt-kernel-mode-driver.md)，则 NATIVE 为默认值。  
  
 POSIX  
 与 Windows NT 中的 POSIX 子系统一起运行的应用程序。  
  
 WINDOWS  
 应用程序不需要控制台，原因很可能是它会创建自己的窗口来与用户进行交互。  如果为本机代码定义了 `WinMain` 或 `wWinMain`，或为托管代码定义了 `WinMain(HISTANCE *, HINSTANCE *, char *, int)` 或 `wWinMain(HINSTANCE *, HINSTANCE *, wchar_t *, int)`，则 WINDOWS 是默认值。  
  
 `Major` 和 `minor`（可选）  
 指定所需的子系统的最低版本。  参数是介于 0 至 65,535 范围内的十进制数。  有关更多信息，请参见"备注"。  版本号没有上限。  
  
## 备注  
 \/SUBSYSTEM 选项为可执行文件指定环境。  
  
 子系统的选择会影响链接器将选择的入口点符号（即入口点函数）。  
  
 子系统的可选最低与默认 `major` 和 `minor` 版本号如下。  
  
|Subsystem|最低|默认|  
|---------------|--------|--------|  
|BOOT\_APPLICATION|1.0|1.0|  
|CONSOLE|5.01 \(x86\) 5.02 \([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]\) 6.02 \(ARM\)|6.00 \(x86, [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]\) 6.02 \(ARM\)|  
|WINDOWS|5.01 \(x86\) 5.02 \([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]\) 6.02 \(ARM\)|6.00 \(x86, [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]\) 6.02 \(ARM\)|  
|NATIVE \(with DRIVER:WDM\)|1.00 \(x86\) 1.10 \([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)], ARM\)|1.00 \(x86\) 1.10 \([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)], ARM\)|  
|NATIVE \(without \/DRIVER:WDM\)|4.00 \(x86\) 5.02 \([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]\) 6.02 \(ARM\)|4.00 \(x86\) 5.02 \([!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]\) 6.02 \(ARM\)|  
|POSIX|1.0|19.90|  
|EFI\_APPLICATION、EFI\_BOOT\_SERVICE\_DRIVER、EFI\_ROM, EFI\_RUNTIME\_DRIVER|1.0|1.0|  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择 Linker 文件夹。  
  
3.  选择“系统”属性页。  
  
4.  修改 `SubSystem` 属性。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SubSystem%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)