---
title: 优化错误 PG0165 按配置文件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PG0165
dev_langs:
- C++
helpviewer_keywords:
- PG0165
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: acad97411480112d06dadd454d1368dcfdf2c87f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318410"
---
# <a name="profile-guided-optimization-error-pg0165"></a>按配置文件优化错误 PG0165
读取 Filename.pgd: 不支持 PGD 版本 （版本不匹配）。  
  
 PGD 文件是特定于特定的编译器工具集。 使用与用于不同的编译器时，会生成此错误*Filename*.pgd。 此错误指示，此编译器工具集无法使用从数据*Filename*.pgd 来优化当前程序。  
  
 若要解决此问题，重新生成*Filename*.pgd 通过使用当前编译器工具集。