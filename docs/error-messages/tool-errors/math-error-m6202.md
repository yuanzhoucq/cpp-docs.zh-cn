---
title: 数学错误 M6202 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6202
dev_langs:
- C++
helpviewer_keywords:
- M6202
ms.assetid: 4d17045f-c6dc-4705-9512-e9af12c35fb4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4596b9782bc1de0e6ccd52bfcd03965415adb353
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332047"
---
# <a name="math-error-m6202"></a>数学错误 M6202
function: 错误  
  
 给定的函数的自变量为此函数的奇点值。 没有为该参数定义函数。  
  
 此错误调用`_matherr`函数名称、 其参数与错误类型的函数。 您可以重新编写`_matherr`函数以自定义的某些运行时浮点数学错误处理。