---
title: 编译器警告 （等级 C4931 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4931
dev_langs:
- C++
helpviewer_keywords:
- C4931
ms.assetid: cfbf08c7-94e4-4a91-a691-479d1dbe527a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 20e39eda9f06330a84243634eba28fc9d351cafe
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43201537"
---
# <a name="compiler-warning-level-4-c4931"></a>编译器警告（等级 4）C4931

> 我们假定类型库为生成*数*-位指针

与未提供显式信息**ptrsize**的属性[#import](../../preprocessor/hash-import-directive-cpp.md)指令; 编译器得出的结论是，类型库的指针大小是*数*。

默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。