---
title: 链接器工具错误 LNK2039
ms.date: 11/04/2016
f1_keywords:
- LNK2039
helpviewer_keywords:
- LNK2039
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
ms.openlocfilehash: 7712747deb865ec62fa007fcd95ad09630d00cea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194494"
---
# <a name="linker-tools-error-lnk2039"></a>链接器工具错误 LNK2039

正在导入另一个 .obj 中定义的 ref 类 "\<类型 >";应导入或定义此项，但不能同时导入或定义

Ref 类 "<`type`>" 在指定的 .obj 文件中导入，但也在另一个 .obj 文件中进行了定义。 此情况可能导致运行时失败或其他意外行为。

### <a name="to-correct-this-error"></a>更正此错误

1. 检查是否必须在其他 .obj 文件中定义“`type`”并检查是否必须从 .winmd 文件导入它。

1. 移除定义或导入。

## <a name="see-also"></a>另请参阅

[链接器工具错误和警告](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)<br/>
[链接器工具错误 LNK1332](../../error-messages/tool-errors/linker-tools-error-lnk1332.md)
