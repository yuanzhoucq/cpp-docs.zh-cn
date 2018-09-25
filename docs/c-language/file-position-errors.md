---
title: 文件位置错误 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- file pointers [C++], file position errors
ms.assetid: d5e59d8b-08c0-4927-a338-0b2d8234ce24
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8def11317548bfd6e70badab4563891c1b6f864d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031896"
---
# <a name="file-position-errors"></a>文件位置错误

**ANSI 4.9.9.1, 4.9.9.4** 失败时，`fgetpos` 或 `ftell` 函数设置的宏 `errno` 的值

当 `fgetpos` 或 `ftell` 失败时，`errno` 将设置为清单常量 `EINVAL`（如果位置无效）或 `EBADF`（如果文件数量错误）。 常量是在 ERRNO.H 中定义的。

## <a name="see-also"></a>请参阅

[库函数](../c-language/library-functions.md)
