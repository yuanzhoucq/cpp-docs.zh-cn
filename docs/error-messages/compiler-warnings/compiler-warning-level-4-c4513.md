---
title: 编译器警告 （等级 C4513 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4513
dev_langs:
- C++
helpviewer_keywords:
- C4513
ms.assetid: 6877334a-f30a-4184-9483-dac3348737a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 75ae1c94d7a11fc9bb0049333c65a6677b04778a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087378"
---
# <a name="compiler-warning-level-4-c4513"></a>编译器警告（等级 4）C4513

class： 未能生成析构函数

编译器无法生成默认析构函数为给定的类;创建没有析构函数。 析构函数是不能由派生类访问基类中。 如果基类具有私有析构函数，使其公共或受保护。