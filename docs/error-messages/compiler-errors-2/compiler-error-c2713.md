---
title: 编译器错误 C2713 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2713
dev_langs:
- C++
helpviewer_keywords:
- C2713
ms.assetid: bae9bee3-b4b8-4be5-b6a5-02df587a7278
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a40c248226cd8f863bb099d16272dfa149f1dc2c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102705"
---
# <a name="compiler-error-c2713"></a>编译器错误 C2713

只有一个窗体的每个函数允许异常处理

不能使用结构化的异常处理 (`__try`/`__except`) 和 c + + 异常处理 (`try`/`catch`) 在同一函数中。