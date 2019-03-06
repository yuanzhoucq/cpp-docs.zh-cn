---
title: /MANIFESTUAC（将 UAC 信息嵌入到清单中）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.UACUIAccess
- VC.Project.VCLinkerTool.UACExecutionLevel
- VC.Project.VCLinkerTool.EnableUAC
helpviewer_keywords:
- /MANIFESTUAC linker option
- MANIFESTUAC linker option
- -MANIFESTUAC linker option
ms.assetid: 2d243c39-fa13-493c-b56f-d0d972a1603a
ms.openlocfilehash: 8ae9d18bb0fe2172886ef24250d53cf76851bbba
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57420422"
---
# <a name="manifestuac-embeds-uac-information-in-manifest"></a>/MANIFESTUAC（将 UAC 信息嵌入到清单中）

指定是否将用户帐户控制 (UAC) 信息嵌入到程序清单中。

## <a name="syntax"></a>语法

```
/MANIFESTUAC
/MANIFESTUAC:NO
/MANIFESTUAC:fragment
/MANIFESTUAC:level=_level
/MANIFESTUAC:uiAccess=_uiAccess
```

### <a name="parameters"></a>参数

*fragment*<br/>
一个字符串，包含`level`和`uiAccess`值。 有关详细信息，请参阅本主题后面备注部分。

*_level*<br/>
之一*asInvoker*， *highestAvailable*，或*requireAdministrator*。 默认值为 asInvoker。 有关详细信息，请参阅本主题后面备注部分。

*_uiAccess*<br/>
**true**如果您希望应用程序来绕过用户界面保护级别并将输入到桌面上的更高权限窗口; 否则为**false**。 默认情况下**false**。 设置为 **，则返回 true**仅为用户界面辅助功能应用程序。

## <a name="remarks"></a>备注

如果指定命令行上的多个 /MANIFESTUAC 选项，请输入最后一个优先。

/MANIFESTUAC:level 的选项如下所示：

- `asInvoker`：应用程序将使用与启动它的进程相同的权限运行。 将应用程序可以通过选择提升到更高的权限级别**以管理员身份运行**。

- 最高可用性：应用程序将使用它可以最高的权限级别运行。 如果启动应用程序的用户是 Administrators 组的成员，此选项等同于 requireAdministrator。 如果最高可用权限级别比打开过程级别更高，系统将提示输入凭据。

- requireAdministrator:应用程序将使用管理员权限运行。 启动应用程序的用户必须是 Administrators 组的成员。 如果打开过程未使用管理权限运行，系统将提示输入凭据。

通过使用 /MANIFESTUAC:fragment 选项，可以在一个步骤中指定的级别和 uiAccess 值。 片段必须采用以下形式：

```
"level=[ asInvoker | highestAvailable | requireAdministrator ] uiAccess=[ true | false ]"
```

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 展开“配置属性”节点。

1. 展开**链接器**节点。

1. 选择**清单文件**属性页。

1. 修改**启用用户帐户控制 (UAC)**， **UAC 执行级别**，并**UAC 绕过 UI 保护**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

1. 请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableUAC%2A>、<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACExecutionLevel%2A>和<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACUIAccess%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)
