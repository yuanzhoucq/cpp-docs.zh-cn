---
title: 命令行错误 D8037 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8037
dev_langs:
- C++
helpviewer_keywords:
- D8037
ms.assetid: acddaaa0-bd84-426f-a37b-8f680b379c9d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 38bbb8e85f0bb11af3846435f31cfc4223a39f16
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086312"
---
# <a name="command-line-error-d8037"></a>命令行错误 D8037

无法创建临时 il 文件;清除临时目录中的旧 il 文件

没有足够的空间来创建临时的编译器中间文件。 若要纠正此错误，删除任何旧的 MSIL 文件中指定的目录**TMP**环境变量。 这些文件将窗体 _CL_hhhhhhhh.ss，其中 h 表示随机的十六进制数字，ss 表示 IL 文件的类型。 此外，请确保使用最新的操作系统修补程序更新您的计算机。

## <a name="see-also"></a>请参阅

[命令行错误 D8000 - D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)<br/>
[编译器选项](../../build/reference/compiler-options.md)