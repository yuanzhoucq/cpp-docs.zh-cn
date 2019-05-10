---
title: 链接器工具错误 LNK2039
ms.date: 11/04/2016
f1_keywords:
- LNK2039
helpviewer_keywords:
- LNK2039
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
ms.openlocfilehash: 57d0c101358f84816c8d0cf96eb5137833df0b48
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298735"
---
# <a name="linker-tools-error-lnk2039"></a>链接器工具错误 LNK2039

正在导入 ref 类\<类型 > another.obj 中定义; 它应导入或定义，而不是同时

Ref 类 <`type`>' 指定的.obj 文件中导入，但也是在另一个.obj 文件中。 此情况可能导致运行时失败或其他意外行为。

### <a name="to-correct-this-error"></a>更正此错误

1. 检查是否必须在其他 .obj 文件中定义“`type`”并检查是否必须从 .winmd 文件导入它。

1. 移除定义或导入。

## <a name="see-also"></a>请参阅

[链接器工具错误和警告](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)<br/>
[链接器工具错误 LNK1332](../../error-messages/tool-errors/linker-tools-error-lnk1332.md)