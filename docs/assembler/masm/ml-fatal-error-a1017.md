---
title: ML 错误 A1017
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A1017
helpviewer_keywords:
- A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
ms.openlocfilehash: 523fed26afae5a88c5f154283487d3453a2e48c7
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318054"
---
# <a name="ml-fatal-error-a1017"></a>ML 错误 A1017

**缺少源文件名**

ML 找不到要汇编或传递到链接器的文件。

如果不指定要操作的文件名，则会生成 ML 命令行选项。 若要组合不具有 .asm 扩展名的文件，请使用 **/Ta**命令行选项。

如果 ML 环境变量包含命令行选项，则还可以通过调用不带参数的 ML 来生成此错误。

## <a name="see-also"></a>另请参阅

[ML 错误消息](ml-error-messages.md)
