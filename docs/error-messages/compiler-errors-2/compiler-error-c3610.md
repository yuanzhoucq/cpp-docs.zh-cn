---
title: 编译器错误 C3610 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3610
dev_langs:
- C++
helpviewer_keywords:
- C3610
ms.assetid: 9349a348-9d37-4a00-9eab-481039268d31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b46b3669978ff3735d5a16015ca0a01e65f07ae9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037848"
---
# <a name="compiler-error-c3610"></a>编译器错误 C3610

valuetype： 在调用方法 method 之前必须将值类型装箱

默认情况下，值类型不是托管堆上。 您可以调用方法从.NET 运行时类，如之前`Object`，您需要将值类型移至托管堆。

C3610 才可访问使用已过时的编译器选项 **/clr: oldsyntax**。
