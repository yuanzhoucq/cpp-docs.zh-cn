---
title: -SUBSYSTEM （指定子系统） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /subsystem
- VC.Project.VCLinkerTool.SubSystem
- VC.Project.VCLinkerTool.SubSystemVersion
dev_langs:
- C++
helpviewer_keywords:
- /SUBSYSTEM linker option
- SUBSYSTEM linker option
- -SUBSYSTEM linker option
- subsystem specifications
ms.assetid: d7b133cf-cf22-4da8-ab46-6552702c0b9b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 75e4612104fdc57fd1442f1a35efbf317a60310d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717088"
---
# <a name="subsystem-specify-subsystem"></a>/SUBSYSTEM（指定子系统）

```
/SUBSYSTEM:{BOOT_APPLICATION|CONSOLE|EFI_APPLICATION|
            EFI_BOOT_SERVICE_DRIVER|EFI_ROM|EFI_RUNTIME_DRIVER|NATIVE|
            POSIX|WINDOWS)
            [,major[.minor]]
```

## <a name="arguments"></a>自变量

**BOOT_APPLICATION**<br/>
在 Windows 启动环境中运行的应用程序。 有关启动应用程序的详细信息，请参阅[关于 BCD](/previous-versions/windows/desktop/bcd/about-bcd)。

**控制台**<br/>
Win32 字符模式应用程序。 操作系统提供为控制台应用程序提供控制台。 如果`main`或`wmain`为本机代码中，定义`int main(array<String ^> ^)`为托管代码中，定义或应用程序完全使用生成`/clr:safe`，控制台是默认值。

**EFI_APPLICATION**<br/>
**EFI_BOOT_SERVICE_DRIVER**<br/>
**EFI_ROM**<br/>
**EFI_RUNTIME_DRIVER**<br/>
可扩展固件接口子系统中。 请参阅 EFI 规范的详细信息。 有关示例，请参阅 Intel 网站。 最小和默认版本为 1.0。

**本机**<br/>
用于 Windows NT 内核模式驱动程序。 此选项通常预留给 Windows 系统组件。 如果[/driver: wdm](../../build/reference/driver-windows-nt-kernel-mode-driver.md)指定，本机模式是默认值。

**POSIX**<br/>
使用 Windows NT 中的 POSIX 子系统运行的应用程序。

**WINDOWS**<br/>
应用程序不需要控制台中，因为它可以创建其自身与用户交互的窗口。 如果`WinMain`或`wWinMain`定义为本机代码，或`WinMain(HISTANCE *, HINSTANCE *, char *, int)`或`wWinMain(HINSTANCE *, HINSTANCE *, wchar_t *, int)`定义托管代码中，对于 WINDOWS 是默认值。

*主要*和*次要*<br/>
（可选）指定的子系统所需最低版本。 参数是十进制数字 0 到 65,535 范围内。 请参阅有关详细信息备注。 没有上限的版本号。

## <a name="remarks"></a>备注

**/SUBSYSTEM**选项指定的可执行文件的环境。

子系统的选择会影响的入口点符号 （或入口点函数） 链接器将选择。

可选的最小值和默认*主要*并*次要*子系统版本号如下所示。

|子系统|最低|默认|
|---------------|-------------|-------------|
|BOOT_APPLICATION|1.0|1.0|
|CONSOLE|5.01 (x86) (x64) 5.02 6.02 (ARM)|（x86、 x64） 6.00 6.02 (ARM)|
|窗口|5.01 (x86) (x64) 5.02 6.02 (ARM)|（x86、 x64） 6.00 6.02 (ARM)|
|本机 （带驱动程序： WDM)|(x86) 1.00 1.10 (x64、 ARM)|(x86) 1.00 1.10 (x64、 ARM)|
|本机 （不带 /driver: wdm)|4.00 (x86) (x64) 5.02 6.02 (ARM)|4.00 (x86) (x64) 5.02 6.02 (ARM)|
|POSIX|1.0|19.90|
|EFI_APPLICATION，EFI_BOOT_SERVICE_DRIVER，EFI_ROM EFI_RUNTIME_DRIVER|1.0|1.0|

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。

1. 选择链接器文件夹。

1. 选择**系统**属性页。

1. 修改`SubSystem`属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SubSystem%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)