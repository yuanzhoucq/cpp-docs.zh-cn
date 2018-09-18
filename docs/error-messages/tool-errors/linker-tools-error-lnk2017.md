---
title: 链接器工具错误 LNK2017 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2017
dev_langs:
- C++
helpviewer_keywords:
- LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 80af2bb6475fc37b7feba5b29bfe9c1292740286
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022445"
---
# <a name="linker-tools-error-lnk2017"></a>链接器工具错误 LNK2017

symbol 重定位到领域没有 /largeaddressaware: no 无效

要生成包含 32 位地址的 64 位映像。 若要执行此操作，必须：

- 使用固定的加载地址。

- 将图像限制为 3 GB。

- 指定[/largeaddressaware: no](../../build/reference/largeaddressaware-handle-large-addresses.md)。