---
title: /MANIFESTUAC（将 UAC 信息嵌入到清单中）
ms.date: 06/12/2020
f1_keywords:
- VC.Project.VCLinkerTool.UACUIAccess
- VC.Project.VCLinkerTool.UACExecutionLevel
- VC.Project.VCLinkerTool.EnableUAC
helpviewer_keywords:
- /MANIFESTUAC linker option
- MANIFESTUAC linker option
- -MANIFESTUAC linker option
ms.assetid: 2d243c39-fa13-493c-b56f-d0d972a1603a
ms.openlocfilehash: 96719c6f6f5359afb03b967524b1f65db6dc664a
ms.sourcegitcommit: 8645408c7929558b8162f781776d0908d790a41c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85334939"
---
# <a name="manifestuac-embeds-uac-information-in-manifest"></a>/MANIFESTUAC（将 UAC 信息嵌入到清单中）

指定是否将用户帐户控制 (UAC) 信息嵌入到程序清单中。

## <a name="syntax"></a>语法

> **`/MANIFESTUAC`**\
> **`/MANIFESTUAC:NO`**\
> **`/MANIFESTUAC:`**_`level`_\
> **`/MANIFESTUAC:`**_`uiAccess`_\
> **`/MANIFESTUAC:`**_`fragment`_

### <a name="parameters"></a>参数

**`NO`**<br/>
链接器不会将 UAC 信息嵌入到程序清单中。

*`level`*<br/>
**`level=`** 后跟 **`'asInvoker'`** 、 **`'highestAvailable'`** 或 **`'requireAdministrator'`** 。 默认值为 **`'asInvoker'`** 。 有关详细信息，请参阅[备注](#remarks)部分。

*`uiAccess`*<br/>
**`uiAccess='true'`** 如果希望应用程序绕过用户界面保护级别并将输入放到桌面上的更高权限窗口上，则为;否则为 **`uiAccess='false'`** 。 默认值为 **`uiAccess='false'`** 。 仅将此参数设置为 **`uiAccess='true'`** 适用于用户界面辅助功能的应用程序。

*`fragment`*<br/>
一个包含 *`level`* 和值的字符串 *`uiAccess`* 。 可以选择用双引号引起来。 有关详细信息，请参阅[备注](#remarks)部分。

## <a name="remarks"></a>注解

如果在 **`/MANIFESTUAC`** 命令行上指定了多个选项，则将优先选择最后一个选项。

的选项如下所示 **`/MANIFESTUAC:`** _`level`_ ：

- **`level='asInvoker'`**：应用程序与启动该应用程序的进程在同一权限级别运行。 通过选择 "以**管理员身份运行**"，可以将应用程序提升到更高的权限级别。

- **`level='highestAvailable'`**：应用程序在它可以的最高权限级别运行。 如果启动该应用程序的用户是 Administrators 组的成员，则此选项与相同 **`level='requireAdministrator'`** 。 如果最高可用权限级别高于打开进程的级别，系统将提示输入凭据。

- **`level='requireAdministrator'`**：应用程序使用管理员权限运行。 启动应用程序的用户必须是 Administrators 组的成员。 如果打开进程没有以管理权限运行，则系统会提示输入凭据。

可以 *`level`* *`uiAccess`* 通过使用选项，在一个步骤中同时指定和值 **`/MANIFESTUAC:`** _`fragment`_ 。 片段必须采用以下格式：

> **`/MANIFESTUAC:`** \[ **`"`** ] **`level=`** { **`'asInvoker'`** | **`'highestAvailable'`** | **`'requireAdministrator'`** } **`uiAccess=`** { **`'true'`** | **`'false'`** } \[ **`"`** ]

例如：

**`/MANIFESTUAC:"level='highestAvailable' uiAccess='true'"`**

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**  >  **链接器**  >  **清单文件**" 属性页。

1. 修改 "**启用用户帐户控制（uac）**"、" **uac 执行级别**" 和 " **uac 绕过 UI 保护**" 属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

1. 请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableUAC%2A>、<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACExecutionLevel%2A>和<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACUIAccess%2A>。

## <a name="see-also"></a>另请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
