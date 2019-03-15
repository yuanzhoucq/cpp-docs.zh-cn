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
ms.openlocfilehash: c750fd94e21eec39a25acf216a452faaa277bf7c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811447"
---
# <a name="noentry-no-entry-point"></a>/NOENTRY（无入口点）

```
/NOENTRY
```

## <a name="remarks"></a>备注

/NOENTRY 选项是创建不包含可执行代码的纯资源 DLL 所必需的。 有关详细信息，请参阅[创建 Resource-Only DLL](../creating-a-resource-only-dll.md)。

请使用此选项防止 LINK 将 `_main` 的引用链接到 DLL 中。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 选择**链接器**文件夹。

1. 选择**高级**属性页。

1. 修改**无入口点**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

1. 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ResourceOnlyDLL%2A>。

## <a name="see-also"></a>请参阅

[创建纯资源 DLL](../creating-a-resource-only-dll.md)<br/>
[MSVC 链接器引用](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
