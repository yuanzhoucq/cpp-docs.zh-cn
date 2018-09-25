---
title: 分配零内存 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, zero memory
- zero memory
ms.assetid: 768f2ab9-83a1-4887-8eb5-c094c18489a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc3b7a92cdc8a05c73f15c7cea917d86a3b6bb46
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085051"
---
# <a name="allocating-zero-memory"></a>分配零内存

**ANSI 4.10.3** 请求的大小为零时，`calloc`、`malloc` 或 `realloc` 函数的行为

`calloc`、`malloc` 和 `realloc` 函数接受零作为参数。 不分配实际内存，但会返回有效的指针，并且之后可通过 realloc 修改内存块。

## <a name="see-also"></a>请参阅

[库函数](../c-language/library-functions.md)