---
title: 链接器工具错误 LNK2017
ms.date: 11/04/2016
f1_keywords:
- LNK2017
helpviewer_keywords:
- LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
ms.openlocfilehash: ce5332c2812740ef0b8c7d8e9c64a095d20a4e2b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62299050"
---
# <a name="linker-tools-error-lnk2017"></a>链接器工具错误 LNK2017

symbol 重定位到领域没有 /largeaddressaware: no 无效

要生成包含 32 位地址的 64 位映像。 若要执行此操作，必须：

- 使用固定的加载地址。

- 将图像限制为 3 GB。

- 指定[/largeaddressaware: no](../../build/reference/largeaddressaware-handle-large-addresses.md)。