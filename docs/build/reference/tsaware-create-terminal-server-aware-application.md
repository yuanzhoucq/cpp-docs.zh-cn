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
ms.openlocfilehash: 4b6cebfd30c6572c2ea7d9a0e59625ac8fd66de1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566590"
---
# <a name="tsaware-create-terminal-server-aware-application"></a>/TSAWARE（创建终端服务器识别的应用程序）

```
/TSAWARE[:NO]
```

## <a name="remarks"></a>备注

/TSAWARE 选项在程序映像的可选标头中的 IMAGE_OPTIONAL_HEADER DllCharacteristics 字段中设置的标志。 当设置此标志后，终端服务器将不会向应用程序进行某些更改。

当应用程序不是终端服务器识别 （也称为旧应用程序） 时，终端服务器将进行某些修改到旧应用程序以使其在多用户环境中正常工作。 例如，终端服务器将创建的虚拟 Windows 文件夹，以便每个用户获取 Windows 文件夹，而不获取系统的 Windows 目录。 这使用户访问他们自己的 INI 文件。 此外，终端服务器将进行一些调整到旧应用程序的注册表。 这些修改的终端服务器上的旧应用程序加载缓慢情况。

如果应用程序是终端服务器识别时，它必须既不依赖于 INI 文件也不写入**HKEY_CURRENT_USER**在安装过程中的注册表。

如果您使用 /TSAWARE 并且你的应用程序仍使用 INI 文件，将由系统的所有用户共享文件。 如果这是可接受，则仍可以链接 /TSAWARE; 与应用程序否则，您需要使用 /tsaware: no。

/TSAWARE 选项是默认情况下启用 Windows 和控制台应用程序。 请参阅[/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md)并[/VERSION](../../build/reference/version-version-information.md)有关信息。

/TSAWARE 驱动程序、 Vxd，或 Dll 无效。

如果应用程序已链接与 /TSAWARE，DUMPBIN [/HEADERS](../../build/reference/headers.md)将显示该结果的信息。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。

1. 单击**链接器**文件夹。

1. 单击**系统**属性页。

1. 修改**终端服务器**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TerminalServerAware%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)<br/>
[存储特定于用户的信息](/windows/desktop/TermServ/storing-user-specific-information)<br/>
[在终端服务环境中的旧版应用程序](https://msdn.microsoft.com/library/aa382957.aspx)