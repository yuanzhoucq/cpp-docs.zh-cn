---
title: 编译器警告 （等级 1） C4381 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4381
dev_langs:
- C++
helpviewer_keywords:
- C4381
ms.assetid: f67a6db3-b334-4b2e-8182-b30c7a3c7c32
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 81c61dcbf49beeb41780cdaeff669cf21bfffee9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037822"
---
# <a name="compiler-warning-level-1-c4381"></a>编译器警告（等级 1）C4381

function1： 不能由非公共方法 function2 实现接口方法

类必须实现在接口中的所有函数。 如果其基类中的一个实现该函数，类可以满足此条件。 但是，该函数必须作为公共函数实现。