---
title: /CETCOMPAT （CET 影子堆栈兼容）
ms.date: 02/19/2019
f1_keywords:
- /CETCOMPAT
helpviewer_keywords:
- /CETCOMPAT linker option
- /CETCOMPAT
ms.openlocfilehash: 2c807d91d69b967fd62e01a077711dede5f55c44
ms.sourcegitcommit: 7e011c68ca7547469544fac87001a33a37e1792e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84421295"
---
# <a name="cetcompat-cet-shadow-stack-compatible"></a>/CETCOMPAT （CET 影子堆栈兼容）

指定是否将可执行映像标记为与控制流强制技术（CET）阴影堆栈兼容。

## <a name="syntax"></a>语法

> **/CETCOMPAT** \[**：否**]

## <a name="arguments"></a>自变量

**不**<br/>
指定应将可执行文件标记为与 CET 影子堆栈兼容。

## <a name="remarks"></a>备注

控制流强制技术（CET）影子堆栈是一项计算机处理器功能，它提供的功能可防御基于返回的编程（ROP）的恶意软件攻击。 有关详细信息，请参阅[Intel 控制流强制技术预览](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf)。

**/CETCOMPAT**链接器选项通知链接器将二进制文件标记为 CET 影子堆栈兼容。 **/CETCOMPAT：不**会将二进制文件标记为与 CET 阴影堆栈不兼容。 如果在命令行上指定了这两个选项，则将使用指定的最后一个选项。 此开关目前仅适用于 x86 和 x64 体系结构。

从 Visual Studio 2019 Preview 3 工具集开始，可以使用 **/CETCOMPAT**选项。

### <a name="to-set-the-cetcompat-linker-option-in-visual-studio"></a>在 Visual Studio 中设置/CETCOMPAT 链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**  >  **链接器**  >  **高级**属性" 页。

1. 选择**CET 影子堆栈兼容**的属性。

1. 在下拉控件中，选择 **"是（/CETCOMPAT）"** 启用 EH 继续元数据，或选择 "**否" （/CETCOMPAT： No）** 以禁用它。


### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

此选项没有以编程方式等效的。

## <a name="see-also"></a>另请参阅

[链接器选项](linker-options.md)
