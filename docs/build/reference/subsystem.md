---
title: /SUBSYSTEM
ms.date: 11/04/2016
f1_keywords:
- /subsystem_editbin
helpviewer_keywords:
- /SUBSYSTEM editbin option
- -SUBSYSTEM editbin option
- SUBSYSTEM editbin option
ms.assetid: 515e4cdf-3cc4-4659-8764-1f2757b49215
ms.openlocfilehash: 708bfcce3e6d6616116bcc08441f374b46914c82
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438858"
---
# <a name="subsystem"></a>/SUBSYSTEM

指定可执行映像需要的执行环境。

```
/SUBSYSTEM:{BOOT_APPLICATION|CONSOLE|EFI_APPLICATION|
        EFI_BOOT_SERVICE_DRIVER|EFI_ROM|EFI_RUNTIME_DRIVER|
        NATIVE|POSIX|WINDOWS|WINDOWSCE}[,major[.minor]]
```

## <a name="remarks"></a>备注

此选项编辑映像以指示操作系统必须为执行而调用的子系统。

可以指定以下任何子系统：

**BOOT_APPLICATION**<br/>
在 Windows 启动环境中运行的应用程序。 有关启动应用程序的详细信息，请参阅[关于 BCD WMI 提供程序](/previous-versions/windows/desktop/bcd/about-bcd)。

**控制台**<br/>
Windows 字符模式应用程序。 操作系统提供为控制台应用程序提供控制台。

**EFI_APPLICATION**<br/>
**EFI_BOOT_SERVICE_DRIVER**<br/>
**EFI_ROM**<br/>
**EFI_RUNTIME_DRIVER**<br/>
可扩展固件接口 (EFI) 映像

EFI 子系统选项描述在可扩展固件接口环境中运行的可执行映像。 此环境通常随硬件一起提供，在加载操作系统之前执行。 EFI 映像类型之间的主要区别在于映像加载到的内存位置以及在映像调用返回时执行的操作。 当控制权返回时，会卸载 EFI_APPLICATION 映像。 仅当控制权返回时带有错误代码时，才会卸载 EFI_BOOT_SERVICE_DRIVER 或 EFI_RUNTIME_DRIVER。 EFI_ROM 映像从 ROM 执行。 有关详细信息，请参阅[统一 EFI 论坛](https://www.uefi.org/)网站上的规范。

**本机**<br/>
在没有子系统环境的情况下运行的代码（例如，内核模式设备驱动程序和本机系统进程）。 此选项通常为 Windows 系统功能而保留。

**POSIX**<br/>
在 Windows 中的 POSIX 子系统中运行的应用。

**WINDOWS**<br/>
在 Windows 图形环境中运行的应用。 这包括桌面应用和通用 Windows 平台（UWP）应用。

**WINDOWSCE**<br/>
WINDOWSCE 子系统指示应用要在具有 Windows CE 内核版本的设备上运行。 内核版本包括 PocketPC、Windows Mobile、Windows Phone 7、Windows CE V1.0-6.0R3 和 Windows Embedded Compact 7。

可选的 `major` 和 `minor` 值指定指定子系统所需的最低版本：

- 版本号的整数部分（小数点左侧的部分）由 `major` 表示。

- 版本号的小数部分（小数点右侧的部分）由 `minor` 表示。

- `major` 和 `minor` 的值必须从 0 到 65,535。

子系统的选择会影响程序的默认开始地址。 有关详细信息，请参阅[/ENTRY （入口点符号）](entry-entry-point-symbol.md)，链接器/ENTRY：*function*选项。

有关详细信息，包括每个子系统的主版本号和次版本号的最小值和默认值，请参阅[/SUBSYSTEM](subsystem-specify-subsystem.md)链接器选项。

## <a name="see-also"></a>另请参阅

[EDITBIN 选项](editbin-options.md)
