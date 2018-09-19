---
title: 按配置优化错误 PG0165 |Microsoft Docs
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
ms.openlocfilehash: 332751a123bf7d6414c40b79870b5edf27a3d8a7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084206"
---
# <a name="profile-guided-optimization-error-pg0165"></a>按配置文件优化错误 PG0165

阅读 Filename.pgd: 不支持 PGD 版本 （版本不匹配）。

PGD 文件是特定于特定的编译器工具集。 使用与用于不同的编译器时，会生成此错误*文件名*.pgd。 此错误表示，此编译器工具集不能使用中的数据*文件名*.pgd 来优化当前程序。

若要解决此问题，重新生成*文件名*.pgd 通过使用当前的编译器工具集。