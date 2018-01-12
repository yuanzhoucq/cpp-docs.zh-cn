---
title: "编译器错误 C3552 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3552
dev_langs: C++
helpviewer_keywords: C3552
ms.assetid: 83401524-1bf1-44c0-8aca-a6eb35c4224c
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ca49c6678a147988ee0b2fb0ab57b6883b80539a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3552"></a>编译器错误 C3552
“typename”: 后指定返回类型不能包含“auto”  
  
 如果你使用 `auto` 关键字作为函数返回类型的占位符，必须提供后指定返回类型。 但是，不能使用其他 `auto` 关键字来指定后指定返回类型。 例如，下述代码片段产生错误 C3552。  
  
 `auto myFunction->auto; // C3552`