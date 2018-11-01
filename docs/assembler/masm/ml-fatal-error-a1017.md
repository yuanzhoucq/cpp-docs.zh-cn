---
title: ML 错误 A1017
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A1017
helpviewer_keywords:
- A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
ms.openlocfilehash: 22a16569364760d0cb1d01011405f7a11dd21cac
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560818"
---
# <a name="ml-fatal-error-a1017"></a>ML 错误 A1017

**缺少源文件名**

ML 找不到要组装或将传递给链接器的文件。

为机器学习命令行选项提供无需指定文件名以对其执行操作时，会生成此错误。 若要组合不具有.asm 扩展名的文件，请使用 **/Ta**命令行选项。

如果机器学习环境变量包含命令行选项不带任何参数调用机器学习，也可以生成此错误。

## <a name="see-also"></a>请参阅

[ML 错误消息](../../assembler/masm/ml-error-messages.md)<br/>