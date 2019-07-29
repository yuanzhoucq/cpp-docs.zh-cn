---
title: /MANIFESTINPUT（指定清单输入）
ms.date: 07/24/2019
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
ms.openlocfilehash: 7b7bd54f98003d9158276fcf75fd61ffb5348585
ms.sourcegitcommit: 720b74dddb1cdf4e570d55103158304ee1df81f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2019
ms.locfileid: "68606459"
---
# <a name="manifestinput-specify-manifest-input"></a>/MANIFESTINPUT（指定清单输入）

指定要包含在映像嵌入清单中的清单输入文件。

## <a name="syntax"></a>语法

```
/MANIFESTINPUT:filename
```

### <a name="parameters"></a>参数

*filename*<br/>
要包括在嵌入清单中的清单文件。

## <a name="remarks"></a>备注

**/MANIFESTINPUT**选项指定用于在可执行映像中创建嵌入清单的输入文件的路径。 如果有多个清单输入文件, 请对每个输入文件多次使用开关。 合并清单输入文件以创建嵌入清单。 此选项需要 **/MANIFEST: EMBED**选项。

此选项不能在 Visual Studio 中直接设置。 请改用项目的 "**其他清单文件**" 属性来指定要包含的其他清单文件。 有关详细信息, 请参阅[清单工具属性页](manifest-tool-property-pages.md)。

## <a name="see-also"></a>请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
