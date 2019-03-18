---
title: /MANIFESTFILE（命名清单文件）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.ManifestFile
helpviewer_keywords:
- MANIFESTFILE linker option
- -MANIFESTFILE linker option
- /MANIFESTFILE linker option
ms.assetid: befa5ab2-a9cf-4c9b-969a-e7b4a930f08d
ms.openlocfilehash: e75c6d8171aae22312ba6aaa2d4304d831ec6d0f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813833"
---
# <a name="manifestfile-name-manifest-file"></a>/MANIFESTFILE（命名清单文件）

```
/MANIFESTFILE:filename
```

## <a name="remarks"></a>备注

/MANIFESTFILE 允许您更改清单文件的默认名称。  清单文件的默认名称是追加有.manifest 的文件名。

/MANIFESTFILE 不会影响如果还未与链接[/manifest](manifest-create-side-by-side-assembly-manifest.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 展开“配置属性”节点。

1. 展开**链接器**节点。

1. 选择**清单文件**属性页。

1. 修改**清单文件**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

1. 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ManifestFile%2A>。

## <a name="see-also"></a>请参阅

[MSVC 链接器引用](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
