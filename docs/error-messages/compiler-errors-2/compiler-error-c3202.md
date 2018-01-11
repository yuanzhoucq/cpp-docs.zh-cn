---
title: "编译器错误 C3202 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3202
dev_langs: C++
helpviewer_keywords: C3202
ms.assetid: 23528a0c-5493-4804-9789-cd3c38e49fb9
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6d244cb85c6f149d47b16458f0dcd1a02af6af99
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3202"></a>编译器错误 C3202
“arg name”：模板参数“parameter”的默认参数无效，应为类模板  
  
 你向模板参数传递的默认参数无效。  
  
 下面的示例生成 C3202：  
  
```  
// C3202.cpp  
template<typename T>  
class X  
{  
};  
  
class Z  
{  
};  
  
template<template<typename U> class T1 = Z, typename T2> // C3202  
class Y  
{  
};  
```