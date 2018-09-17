---
title: /APPCONTAINER （UWP/Microsoft Store 应用程序） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 9a432db5-7640-460b-ab18-6f61fa7daf6f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d52148f14c21773a6fe93c3909c91f80c3c3650
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726565"
---
# <a name="appcontainer-microsoft-store-app"></a>/APPCONTAINER （Microsoft Store 应用程序）

指定链接器是否创建必须在应用程序容器中运行的可执行映像。

## <a name="syntax"></a>语法

```
/APPCONTAINER[:NO]
```

## <a name="remarks"></a>备注

默认情况下，/APPCONTAINER 是关闭的。

此选项修改可执行文件以指示是否必须在 appcontainer 进程隔离环境中运行应用程序。 必须在 appcontainer 环境中运行的应用程序指定 /APPCONTAINER-例如，一个通用 Windows 平台 (UWP) 或 Windows Phone 8.x 应用。 （会自动设置选项在 Visual Studio 中从模板创建通用 Windows 应用时。）对于桌面应用中，指定 /appcontainer: no 或只需省略该选项。

在 Windows 8 中引入了 /APPCONTAINER 选项。

### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中设置此链接器选项

1. 打开项目“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 展开“配置属性”节点。

1. 展开**链接器**节点。

1. 选择**命令行**属性页。

1. 在中**其他选项**，输入`/APPCONTAINER`或`/APPCONTAINER:NO`。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)