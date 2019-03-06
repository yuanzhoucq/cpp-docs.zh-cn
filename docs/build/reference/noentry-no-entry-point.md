---
title: /NOENTRY（无入口点）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.ResourceOnlyDLL
- /noentry
helpviewer_keywords:
- entry points [C++], linker specifying
- -NOENTRY linker option
- resource-only DLLs [C++], creating
- NOENTRY linker option
- /NOENTRY linker option [C++]
- DLLs [C++], creating
ms.assetid: 0214dd41-35ad-43ab-b892-e636e038621a
ms.openlocfilehash: 28a9e09c4a78623c2cda2f8802ba4e1c1435d093
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423737"
---
# <a name="noentry-no-entry-point"></a>/NOENTRY（无入口点）

```
/NOENTRY
```

## <a name="remarks"></a>备注

/NOENTRY 选项是创建不包含可执行代码的纯资源 DLL 所必需的。 有关详细信息，请参阅[创建 Resource-Only DLL](../../build/creating-a-resource-only-dll.md)。

请使用此选项防止 LINK 将 `_main` 的引用链接到 DLL 中。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。

1. 选择**链接器**文件夹。

1. 选择**高级**属性页。

1. 修改**无入口点**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

1. 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ResourceOnlyDLL%2A>。

## <a name="see-also"></a>请参阅

[创建纯资源 DLL](../../build/creating-a-resource-only-dll.md)<br/>
[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)
