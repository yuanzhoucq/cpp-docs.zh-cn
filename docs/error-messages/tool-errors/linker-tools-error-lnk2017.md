---
title: 链接器工具错误 LNK2017
ms.date: 11/04/2016
f1_keywords:
- LNK2017
helpviewer_keywords:
- LNK2017
ms.assetid: f7c21733-b0fb-4888-a295-9b453ba6ee77
ms.openlocfilehash: 02e80de5c34809a331003f3b0fb28d32e138a531
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194728"
---
# <a name="linker-tools-error-lnk2017"></a>链接器工具错误 LNK2017

"symbol" 重定位到 "段" 无效，没有/LARGEADDRESSAWARE： NO

你正在尝试使用32位地址生成64位映像。 要这样做，必须：

- 使用固定的加载地址。

- 将图像限制为 3 GB。

- 指定[/largeaddressaware： no](../../build/reference/largeaddressaware-handle-large-addresses.md)。
