---
title: "编译器错误 C2708 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2708
dev_langs: C++
helpviewer_keywords: C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 495fd9aeaad785edd8653e46ae666f60c337b12d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2708"></a>编译器错误 C2708
identifier： 以字节为单位的实际参数长度不同于上一个调用或引用  
  
 A [__stdcall](../../cpp/stdcall.md)函数的前面必须是原型。 否则为编译器会解释首次作为原型函数调用，并且当编译器遇到不匹配的调用时发生此错误。  
  
 若要解决此错误，请添加一个函数原型。