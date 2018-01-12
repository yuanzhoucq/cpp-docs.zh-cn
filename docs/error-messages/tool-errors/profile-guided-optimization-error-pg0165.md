---
title: "优化错误 PG0165 按配置文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PG0165
dev_langs: C++
helpviewer_keywords: PG0165
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 32b9f5f3ee335aac0a8382377aa850c3b91a27a0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="profile-guided-optimization-error-pg0165"></a>按配置文件优化错误 PG0165
读取 Filename.pgd: 不支持 PGD 版本 （版本不匹配）。  
  
 PGD 文件是特定于特定的编译器工具集。 使用与用于不同的编译器时，会生成此错误*Filename*.pgd。 此错误指示，此编译器工具集无法使用从数据*Filename*.pgd 来优化当前程序。  
  
 若要解决此问题，重新生成*Filename*.pgd 通过使用当前编译器工具集。