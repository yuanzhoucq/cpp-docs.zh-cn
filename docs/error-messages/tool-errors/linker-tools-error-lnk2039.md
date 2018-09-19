---
title: 链接器工具错误 LNK2039 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2039
dev_langs:
- C++
helpviewer_keywords:
- LNK2039
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac4fdde90911427a1a193bfb6f3a950a7bdcf180
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081788"
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