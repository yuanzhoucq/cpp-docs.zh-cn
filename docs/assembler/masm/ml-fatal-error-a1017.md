---
title: ML 错误 A1017 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1017
dev_langs:
- C++
helpviewer_keywords:
- A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb98eab68da417526a75beaa57870ce906c85a8d
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43688554"
---
# <a name="ml-fatal-error-a1017"></a>ML 错误 A1017

**缺少源文件名**

ML 找不到要组装或将传递给链接器的文件。

为机器学习命令行选项提供无需指定文件名以对其执行操作时，会生成此错误。 若要组合不具有.asm 扩展名的文件，请使用 **/Ta**命令行选项。

如果机器学习环境变量包含命令行选项不带任何参数调用机器学习，也可以生成此错误。

## <a name="see-also"></a>请参阅

[ML 错误消息](../../assembler/masm/ml-error-messages.md)<br/>