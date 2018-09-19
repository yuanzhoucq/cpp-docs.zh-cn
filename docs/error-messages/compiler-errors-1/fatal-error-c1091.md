---
title: 错误 C1091 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1091
dev_langs:
- C++
helpviewer_keywords:
- C1091
ms.assetid: 812d4201-9154-48b0-b9af-5959c082ca33
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e93c2e6c26f8704e700465fb706867129847a460
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104228"
---
# <a name="fatal-error-c1091"></a>错误 C1091

编译器限制：字符串长度超过“length”个字节

字符串常量超过当前的字符串长度限制。

你可能希望将静态字符串拆分为两个（或更多）变量，以及使用 [strcpy_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) 在声明或在运行时联接结果。