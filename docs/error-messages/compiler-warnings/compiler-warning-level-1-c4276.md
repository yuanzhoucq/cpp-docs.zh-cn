---
title: "编译器警告 （等级 1） C4276 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4276
dev_langs:
- C++
helpviewer_keywords:
- C4276
ms.assetid: 9d738c2d-29e5-408a-b9ff-be1a850b2238
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: af9a32da86a0ea9e530af03a2175976d4cd9f091
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4276"></a>编译器警告（等级 1）C4276
function： 不提供原型;假定没有参数  
  
 当你执行与函数的地址[__stdcall](../../cpp/stdcall.md)调用约定，你必须提供原型，以便编译器可以创建函数的修饰的名称。 由于*函数*不具有任何原型，编译器，创建修饰的名时，假定函数没有任何参数。