---
title: "编译器错误 C2338 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2338
dev_langs: C++
helpviewer_keywords: C2338
ms.assetid: 49bba575-1de4-4963-86c6-ce3226a2ba51
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3b5f8773daa61b2ac7703b1ee0e5672818278e87
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2338"></a>编译器错误 C2338  
  
> *错误消息*  
  
此错误可能由`static_assert`编译过程中的出错。 通过提供消息`static_assert`参数。   
  
此外可以通过外部提供程序与编译器生成此错误消息。 在大多数情况下，这些错误由特性提供程序 DLL，如 ATLPROV 进行报告。 此消息的某些常见形式包括：

> *属性*Atl 特性提供程序： 错误 ATL*数**消息*  
  
> 属性的用法不正确*属性*
  
> *用法*： 特性的使用率的格式不正确  
  
这些错误通常是不可恢复，并且可能跟严重的编译器错误。  
  
若要修复这些问题，请更正属性用法。 例如，在某些情况下，属性参数必须声明后，才可以使用。 如果提供 ATL 错误号，请检查该错误的更具体的信息的文档。  
