---
title: 编译器警告 （等级 1） C4910 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e6db959e467ea449a66feb3ee07c202f4dee002
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018946"
---
# <a name="compiler-warning-level-1-c4910"></a>编译器警告（等级 1）C4910

\<标识符 >: __declspec （dllexport） 和 extern 在显式实例化上不兼容

名为的显式模板实例化*\<标识符 >* 由已修改`__declspec(dllexport)`和`extern`关键字。 但是，这些关键字互斥。 `__declspec(dllexport)` 关键字表示实例化模板类，而 `extern` 关键字表示不要自动实例化模板类。

## <a name="see-also"></a>请参阅

[显式实例化](../../cpp/explicit-instantiation.md)<br/>
[dllexport、dllimport](../../cpp/dllexport-dllimport.md)<br/>
[一般规则和限制](../../cpp/general-rules-and-limitations.md)