---
title: /NOLOGO（取消显示启动版权标志）（链接器）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.SuppressStartupBanner
- /nologo
helpviewer_keywords:
- suppress startup banner linker option
- -NOLOGO linker option
- /NOLOGO linker option
- copyright message
- version numbers, preventing linker display
- banners, suppressing startup
- NOLOGO linker option
ms.assetid: 3b20dddd-eca6-4545-a331-9f70bf720197
ms.openlocfilehash: 1b966c1f7af556a85aadcafaa8ed43da5b3f75df
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422151"
---
# <a name="nologo-suppress-startup-banner-linker"></a>/NOLOGO（取消显示启动版权标志）（链接器）

```
/NOLOGO
```

## <a name="remarks"></a>备注

/NOLOGO 选项禁止显示版权消息和版本数。

此选项还将取消回显命令文件。 有关详细信息，请参阅[LINK 命令文件](../../build/reference/link-command-files.md)。

默认情况下，此信息发送到输出窗口，链接器。 在命令行中，它发送到标准输出，并可以定向到一个文件。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 只应从命令行使用此选项。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

1. 不能以编程方式更改此链接器选项。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)
