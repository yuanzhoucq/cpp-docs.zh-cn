---
title: /DYNAMICBASE（使用地址空间布局随机化功能）
ms.date: 06/12/2018
f1_keywords:
- VC.Project.VCLinkerTool.RandomizedBaseAddress
helpviewer_keywords:
- -DYNAMICBASE linker option
- /DYNAMICBASE linker option
- DYNAMICBASE linker option
ms.assetid: 6c0ced8e-fe9c-4b63-b956-eb8a55fbceb2
ms.openlocfilehash: 47d23ac6f9234e095a1733a8d4078840318cce4b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512393"
---
# <a name="dynamicbase-use-address-space-layout-randomization"></a>/DYNAMICBASE（使用地址空间布局随机化功能）

指定是否生成可执行映像可以是随机重新设定基址在加载时使用了第一次 Windows Vista 中提供的 Windows 的地址空间布局随机化 (ASLR) 功能。

## <a name="syntax"></a>语法

> **/DYNAMICBASE**[**： 否**]

## <a name="remarks"></a>备注

**/DYNAMICBASE**选项修改的标头*可执行映像*，.dll 或.exe 文件，以指示是否应为随机重新设定基址在加载时，应用程序，并启用虚拟地址分配随机化，这会影响的虚拟内存位置的堆，堆栈和其他操作系统分配。 **/DYNAMICBASE**选项适用于 32 位和 64 位映像。 在 Windows Vista 和更高版本操作系统上支持 ASLR。 早期版本的操作系统忽略该选项。

默认情况下 **/DYNAMICBASE**已启用。 若要禁用此选项，请使用 **/dynamicbase: no**。 **/DYNAMICBASE**是所必需的选项[/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)选项产生任何影响。

### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中设置此链接器选项

1. 打开项目“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **高级**属性页。

1. 修改**随机化基址**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RandomizedBaseAddress%2A>。

## <a name="see-also"></a>请参阅

- [设置链接器选项](../../build/reference/setting-linker-options.md)
- [链接器选项](../../build/reference/linker-options.md)
- [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)
- [Windows ISV 软件安全防御措施](https://msdn.microsoft.com/library/bb430720.aspx)