---
title: /MANIFESTINPUT（指定清单输入）
ms.date: 07/24/2019
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
ms.openlocfilehash: d7c8351c915f5666ada9939df686c81c86ab89ba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337492"
---
# <a name="manifestinput-specify-manifest-input"></a>/MANIFESTINPUT（指定清单输入）

指定要包含在图像中的清单中的清单输入文件。

## <a name="syntax"></a>语法

```
/MANIFESTINPUT:filename
```

### <a name="parameters"></a>参数

*文件名*<br/>
要包含在嵌入清单中的清单文件。

## <a name="remarks"></a>备注

**/MANIFESTINPUT**选项指定用于在可执行映像中创建嵌入清单的输入文件的路径。 如果您有多个清单输入文件，请使用该开关多次 — 每个输入文件一次。 合并清单输入文件以创建嵌入的清单。 此选项需要 **/MANIFEST：EMBED**选项。

无法直接在可视化工作室中设置此选项。 相反，请使用项目**的其他清单文件**属性指定要包括的其他清单文件。 有关详细信息，请参阅[清单工具属性页](manifest-tool-property-pages.md)。

## <a name="see-also"></a>另请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
