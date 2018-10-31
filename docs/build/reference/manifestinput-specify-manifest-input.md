---
title: /MANIFESTINPUT（指定清单输入）
ms.date: 11/04/2016
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
ms.openlocfilehash: 30e0d4b71943dec8e0efe9112caf7cdf57f66809
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442687"
---
# <a name="manifestinput-specify-manifest-input"></a>/MANIFESTINPUT（指定清单输入）

指定要在图像中嵌入的清单中包含的清单输入的文件。

## <a name="syntax"></a>语法

```
/MANIFESTINPUT:filename
```

### <a name="parameters"></a>参数

*filename*<br/>
要在嵌入的清单中包含的清单文件。

## <a name="remarks"></a>备注

**/MANIFESTINPUT**选项用于指定要用于创建可执行映像中嵌入的清单输入文件的路径。 如果有多个清单输入文件，多次使用切换 — 一次针对每个输入文件。 清单输入的文件经过合并以创建嵌入的清单。 此选项需要 **/manifest： 嵌入**选项。

不能直接在 Visual Studio 中设置此选项。 请改用**附加清单文件**要指定其他要包含的清单文件的项目的属性。 有关详细信息，请参阅[输入和输出、 清单工具、 配置属性\<项目名称 > 属性页对话框](../../ide/input-and-output-manifest-tool.md)。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)