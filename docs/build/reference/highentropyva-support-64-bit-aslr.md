---
title: /HIGHENTROPYVA (支持 64 位 ASLR) |Microsoft Docs
ms.custom: ''
ms.date: 06/12/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: fe35f9f7-d28e-4694-9aeb-a79db06168e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 66fe8f20631d576264eab836f822a414c1244d5b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43223411"
---
# <a name="highentropyva-support-64-bit-aslr"></a>/HIGHENTROPYVA（支持 64 位 ASLR）

指定可执行映像是否支持高熵 64 位地址空间布局随机化 (ASLR)。

## <a name="syntax"></a>语法

> **/HIGHENTROPYVA**[**： 否**]

## <a name="remarks"></a>备注

**/HIGHENTROPYVA**修改的标头*可执行映像*，.dll 文件或.exe 文件，以指示 ASLR 是否可以使用整个 64 位地址空间。 当在可执行文件和所有依赖的模块上执行此选项时，支持 64 位 ASLR 的操作系统可在加载时通过使用 64 位虚拟地址空间来变基可执行映像。 更大的地址空间使攻击者更难猜到特定内存区域的位置。

默认情况下 **/HIGHENTROPYVA**启用为 64 位可执行映像。 此选项需要[/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)，其中还启用了默认情况下为 64 位映像。 **/HIGHENTROPYVA**不是适用于 32 位可执行映像，其中链接器会忽略选项。 若要显式禁用此选项，请使用 **/highentropyva: no**。

有关 **/HIGHENTROPYVA**若要在加载时，会影响[/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)还必须启用。 **/DYNAMICBASE**默认情况下，启用，需要启用 Windows Vista 和更高版本操作系统中的 ASLR。 早期 Windows 版本忽略此标志。

### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中设置此链接器选项

1. 打开项目“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **命令行**属性页。

1. 在中**其他选项**，输入`/HIGHENTROPYVA`或`/HIGHENTROPYVA:NO`。

## <a name="see-also"></a>请参阅

- [设置链接器选项](../../build/reference/setting-linker-options.md)
- [链接器选项](../../build/reference/linker-options.md)
- [/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)
- [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)
- [Windows ISV 软件安全防御措施](https://msdn.microsoft.com/library/bb430720.aspx)
