---
title: /CLRTHREADATTRIBUTE（设置 CLR 线程特性）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.CLRThreadAttribute
helpviewer_keywords:
- /CLRTHREADATTRIBUTE linker option
- -CLRTHREADATTRIBUTE linker option
ms.assetid: 4907e9ef-5031-446c-aecf-0a0b32fae1e8
ms.openlocfilehash: f1a637f74cf1da608149779821a25340d35f8739
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417146"
---
# <a name="clrthreadattribute-set-clr-thread-attribute"></a>/CLRTHREADATTRIBUTE（设置 CLR 线程特性）

显式指定用于 CLR 程序入口点的线程特性。

## <a name="syntax"></a>语法

```
/CLRTHREADATTRIBUTE:{STA|MTA|NONE}
```

#### <a name="parameters"></a>参数

**MTA**<br/>
MTAThreadAttribute 特性应用于您的程序的入口点。

**无**<br/>
与不指定 /CLRTHREADATTRIBUTE 相同。  允许公共语言运行时 (CLR) 设置默认线程特性。

**STA**<br/>
STAThreadAttribute 特性应用于您的程序的入口点。

## <a name="remarks"></a>备注

设置将 thread 特性有效时才生成.exe，因为它会影响主线程的入口点。

如果使用的默认入口点 （main 或 wmain，例如） 指定的线程模型是通过 /CLRTHREADATTRIBUTE 或上来将线程处理特性 （STAThreadAttribute 或 MTAThreadAttribute） 上的默认入口函数。

如果使用非默认入口点，指定线程模型使用 /CLRTHREADATTRIBUTE 或放置线程处理特性，可以在非默认入口函数，并指定使用的非默认入口点[/ENTRY](../../build/reference/entry-entry-point-symbol.md).

如果 /CLRTHREADATTRIBUTE 使用指定的线程模型不一致的源代码中指定的线程处理模型，将忽略 /CLRTHREADATTRIBUTE 链接器并将其应用源代码中指定的线程处理模型。

如果 CLR 程序承载使用单线程的 COM 对象，它将使用单线程处理，例如，你所必需的。  如果您的 CLR 程序使用多线程处理，它不能承载使用单线程的 COM 对象。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 展开“配置属性”节点。

1. 展开**链接器**节点。

1. 选择**高级**属性页。

1. 修改**CLR 线程特性**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

1. 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRThreadAttribute%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)
