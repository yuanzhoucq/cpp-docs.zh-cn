---
title: /ALLOWISOLATION（清单查找）
ms.date: 11/04/2016
f1_keywords:
- /ALLOWISOLATION
- VC.Project.VCLinkerTool.AllowIsolation
helpviewer_keywords:
- -ALLOWISOLATION linker option
- /ALLOWISOLATION linker option
ms.assetid: 6d41851e-b3c1-4bdf-beaa-031773089d6f
ms.openlocfilehash: 7c799f3d44428643bccc2869255ffa4e9d194d70
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493139"
---
# <a name="allowisolation-manifest-lookup"></a>/ALLOWISOLATION（清单查找）

指定清单查找的行为。

## <a name="syntax"></a>语法

```
/ALLOWISOLATION[:NO]
```

## <a name="remarks"></a>备注

**/ALLOWISOLATION: no**指示将加载 dll, 就好像没有清单, 并使链接器在可选标`IMAGE_DLLCHARACTERISTICS_NO_ISOLATION`头的`DllCharacteristics`字段中设置位。

**/ALLOWISOLATION**导致操作系统进行清单查找和加载。

默认值为 **/ALLOWISOLATION** 。

为可执行文件禁用隔离后, Windows 加载程序将不会尝试为新创建的进程查找应用程序清单。 新进程没有默认激活上下文, 即使可执行文件中有清单, 或将其放置在名称为<em>executable</em>的可执行文件所在的同一目录中。

有关详细信息, 请参阅[清单文件引用](/windows/win32/SbsCs/manifest-files-reference)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性** > **链接器** > **清单文件**" 属性页。

1. 修改**Allow 隔离**属性。

## <a name="see-also"></a>请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
