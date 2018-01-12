---
title: "编译器警告 （等级 1） C4445 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4445
dev_langs: C++
helpviewer_keywords: C4445
ms.assetid: 535e92a0-ba08-4dfc-89b2-af2dcdd7caeb
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0e351d23d943d53cef3184a826fecc90c5a28359
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4445"></a>编译器警告（等级 1）C4445
“function”: 在 WinRT 或托管类型中，虚方法不能为私有方法  
  
 如果虚函数是私有函数，则它无法由派生类型访问。 若要修复此错误，请将虚拟成员函数的可访问性更改为受保护或公共。