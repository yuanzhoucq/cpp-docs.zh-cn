---
title: 页 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- PAGE
dev_langs:
- C++
helpviewer_keywords:
- Page directive
ms.assetid: 6654c094-c1f7-4d10-8d9d-902ddd1ac27e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cc2057a850d050795ec605eca8e31b69a0086169
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43692475"
---
# <a name="page"></a>PAGE

第一个指令设置行*长度*和字符*宽度*的程序列表。 如果不给定任何参数时，将生成一个分页符。 第二个指令的节号会递增，并且将页码重置为 1。

## <a name="syntax"></a>语法

> 页 [[*长度*]] [[，*宽度*]]<br/><br/>
> 页 +

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>