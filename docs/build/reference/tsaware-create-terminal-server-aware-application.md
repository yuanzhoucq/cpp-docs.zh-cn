---
title: /TSAWARE（创建终端服务器识别的应用程序）
ms.date: 11/04/2016
f1_keywords:
- /tsaware
- VC.Project.VCLinkerTool.TerminalServerAware
helpviewer_keywords:
- Terminal Server
- /TSAWARE linker option
- Terminal Server, Terminal Server-aware applications
- -TSAWARE linker option
- TSAWARE linker option
ms.assetid: fe1c1846-de5b-4839-b562-93fbfe36cd29
ms.openlocfilehash: 981158125cf978c2f685501117f95553df9c3c89
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498191"
---
# <a name="tsaware-create-terminal-server-aware-application"></a>/TSAWARE（创建终端服务器识别的应用程序）

```
/TSAWARE[:NO]
```

## <a name="remarks"></a>备注

/TSAWARE 选项在程序映像的可选标头的 IMAGE_OPTIONAL_HEADER DllCharacteristics 字段中设置标志。 当设置此标志后，终端服务器将不会向应用程序进行某些更改。

当应用程序不是终端服务器感知 (也称为旧应用程序) 时, 终端服务器会对旧应用程序进行某些修改, 使其在多用户环境中正常工作。 例如, 终端服务器将创建一个虚拟 Windows 文件夹, 以便每个用户获取一个 Windows 文件夹, 而不是获取系统的 Windows 目录。 这样, 用户便可以访问自己的 INI 文件。 此外, 终端服务器还会对旧应用程序的注册表进行一些调整。 这些修改将导致在终端服务器上加载旧应用程序的速度变慢。

如果某个应用程序是终端服务器感知, 则在安装过程中它不能依赖于 INI 文件或写入**HKEY_CURRENT_USER**注册表。

如果你使用/TSAWARE, 但你的应用程序仍然使用 INI 文件, 则这些文件将由系统的所有用户共享。 如果可以接受, 仍可以通过/TSAWARE 链接应用程序;否则, 你需要使用/TSAWARE: NO。

默认情况下, 为 Windows 和控制台应用程序启用/TSAWARE 选项。 有关信息, 请参阅[/SUBSYSTEM](subsystem-specify-subsystem.md)和[/VERSION](version-version-information.md) 。

/TSAWARE 对驱动程序、Vxd 或 Dll 无效。

如果应用程序是与/TSAWARE 链接的, 则 DUMPBIN [/HEADERS](headers.md)将显示该效果的信息。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 单击“链接器”文件夹。

1. 单击 "**系统**" 属性页。

1. 修改 "**终端服务器**" 属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TerminalServerAware%2A>。

## <a name="see-also"></a>请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)<br/>
[存储特定于用户的信息](/windows/win32/TermServ/storing-user-specific-information)<br/>
[终端服务环境中的旧版应用程序](https://msdn.microsoft.com/library/aa382957.aspx)
