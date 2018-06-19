---
title: NMAKE 错误 U1064 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1064
dev_langs:
- C++
helpviewer_keywords:
- U1064
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5573943fc2c274d48768933a634b2c052361a8f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332135"
---
# <a name="nmake-fatal-error-u1064"></a>NMAKE 错误 U1064
找不到的生成文件和指定任何目标  
  
 NMAKE 命令行中没有指定生成文件或目标和当前目录不包含名为生成文件的文件。  
  
 NMAKE 需要生成文件或命令行的目标 （或两者）。 要生成文件提供给 NMAKE，请指定 /F 选项或者放置在当前目录命名生成文件的文件。 NMAKE 可以通过使用推理规则，如果未提供生成文件创建的命令行的目标。