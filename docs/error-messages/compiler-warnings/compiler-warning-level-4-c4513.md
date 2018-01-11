---
title: "编译器警告 （等级 4） C4513 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4513
dev_langs: C++
helpviewer_keywords: C4513
ms.assetid: 6877334a-f30a-4184-9483-dac3348737a4
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c07828569b789c6035b5ea28d47d7fd026341026
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4513"></a>编译器警告（等级 4）C4513
class： 无法生成析构函数  
  
 编译器无法生成给定类; 在默认析构函数已不创建任何析构函数。 析构函数是不可访问到派生的类的基类中。 如果基类具有私有析构函数，使其公共或受保护。