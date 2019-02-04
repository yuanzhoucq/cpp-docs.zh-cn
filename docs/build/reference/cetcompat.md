---
title: / CETCOMPAT （控制流强制技术兼容）
ms.date: 02/01/2019
f1_keywords:
- /CETCOMPAT
helpviewer_keywords:
- /CETCOMPAT linker option
- /CETCOMPAT
ms.openlocfilehash: 3adb147804674b52a5d77030c48567ec04da6aa6
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703403"
---
# <a name="cetcompat-control-flow-enforcement-technology-compatible"></a>/ CETCOMPAT （控制流强制技术兼容）

指定是否将标记为控制流强制技术 (CET) 兼容的可执行映像。

## <a name="syntax"></a>语法

> **/CETCOMPAT**\[**:NO**]

## <a name="arguments"></a>自变量

**NO**<br/>
指定的 executalbe 不应标记与 CET 兼容。

## <a name="remarks"></a>备注

控制流强制技术 (CET) 是一项计算机处理器功能，可提供更有效地防止某些类型的恶意软件攻击的功能。 有关详细信息，请参阅[Intel 控制流强制技术预览](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf)。

**/CETCOMPAT**链接器选项通知链接器将标记作为 CET 兼容二进制文件。 **/CETCOMPAT:NO**将标记为与 cet 证书不兼容的二进制文件。 如果在命令行上指定这两个选项，则使用指定的最后一个。 此开关目前仅适用于 x86 和 x64 体系结构。

**/CETCOMPAT**选项是在 Visual Studio 2019 预览版 3 工具集开始提供。

### <a name="to-set-the-cetcompat-linker-option-in-visual-studio"></a>在 Visual Studio 中设置 /CETCOMPAT 链接器选项

1. 打开**属性页**项目对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **命令行**属性页。

1. 在中**其他选项**框中，添加 **/CETCOMPAT**或 **/CETCOMPAT:NO** ，然后选择**确定**或**应用**若要保存所做的更改。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 此选项不具有编程等效项。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)
