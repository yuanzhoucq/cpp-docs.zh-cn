---
title: 编译器错误 C2708 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2708
dev_langs:
- C++
helpviewer_keywords:
- C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d30b2e5c1856a604ae314316cd71d6acc00a7c74
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33234755"
---
# <a name="compiler-error-c2708"></a>编译器错误 C2708
identifier： 以字节为单位的实际参数长度不同于上一个调用或引用  
  
 A [__stdcall](../../cpp/stdcall.md)函数的前面必须是原型。 否则为编译器会解释首次作为原型函数调用，并且当编译器遇到不匹配的调用时发生此错误。  
  
 若要解决此错误，请添加一个函数原型。