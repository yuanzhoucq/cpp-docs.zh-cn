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
ms.openlocfilehash: 66d6232ed43f9c842ebbb0e22b57c509cf610afa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170054"
---
# <a name="dynamicbase-use-address-space-layout-randomization"></a>/DYNAMICBASE（使用地址空间布局随机化功能）

指定是否生成可在加载时随机变基的可执行映像，该映像使用 windows Vista 中首次提供的 Windows 的地址空间布局随机化（ASLR）功能。

## <a name="syntax"></a>语法

> **/DYNAMICBASE**[ **： NO**]

## <a name="remarks"></a>备注

**/DYNAMICBASE**选项修改*可执行映像*（.dll 或 .exe 文件）的标头，以指示应用程序是否应在加载时随机变基，并启用虚拟地址分配随机化，这会影响堆、堆栈和其他操作系统分配的虚拟内存位置。 **/DYNAMICBASE**选项适用于32位和64位映像。 Windows Vista 和更高版本的操作系统支持 ASLR。 早期的操作系统将忽略此选项。

默认情况下， **/DYNAMICBASE**处于启用状态。 若要禁用此选项，请使用 **/DYNAMICBASE： NO**。 若要使[/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)选项生效， **/DYNAMICBASE**选项是必需的。

### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中设置此链接器选项

1. 打开项目“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1.  > **链接器** > "**高级**" 属性页中选择 "**配置属性**"。

1. 修改 "**随机基址**" 属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RandomizedBaseAddress%2A>。

## <a name="see-also"></a>另请参阅

- [MSVC 链接器参考](linking.md)
- [MSVC 链接器选项](linker-options.md)
- [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)
- [Windows ISV 软件安全防御](https://msdn.microsoft.com/library/bb430720.aspx)
