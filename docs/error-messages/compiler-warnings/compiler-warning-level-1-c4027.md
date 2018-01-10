---
title: "编译器警告 （等级 1） C4027 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4027
dev_langs: C++
helpviewer_keywords: C4027
ms.assetid: f30d57b9-20c4-4284-8686-566d9f0ca7fc
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 22a8a1794a5b80af58a26f07bf58d11a77cb1d5a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4027"></a>编译器警告（等级 1）C4027
未用形参表声明的函数  
  
 函数声明没有形参，但在函数定义中有形参或在调用中有实参。 对此函数的后续调用假定该函数采用函数定义或调用中找到的类型的实参。