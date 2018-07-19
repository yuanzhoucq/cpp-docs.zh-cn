---
title: 编译器警告 （等级 4） C4513 |Microsoft 文档
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
ms.openlocfilehash: 92c3e89204ec30f9c96a5ea03ede5093dd013d0c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292891"
---
# <a name="compiler-warning-level-4-c4513"></a>编译器警告（等级 4）C4513
class： 无法生成析构函数  
  
 编译器无法生成给定类; 在默认析构函数已不创建任何析构函数。 析构函数是不可访问到派生的类的基类中。 如果基类具有私有析构函数，使其公共或受保护。