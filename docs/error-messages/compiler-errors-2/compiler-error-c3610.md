---
title: 编译器错误 C3610
ms.date: 11/04/2016
f1_keywords:
- C3610
helpviewer_keywords:
- C3610
ms.assetid: 9349a348-9d37-4a00-9eab-481039268d31
ms.openlocfilehash: 9965e6420171b2ea48c8fb7bacc0a5a37ea2f227
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344611"
---
# <a name="compiler-error-c3610"></a>编译器错误 C3610

valuetype： 在调用方法 method 之前必须将值类型装箱

默认情况下，值类型不是托管堆上。 您可以调用方法从.NET 运行时类，如之前`Object`，您需要将值类型移至托管堆。

C3610 才可访问使用已过时的编译器选项 **/clr: oldsyntax**。
