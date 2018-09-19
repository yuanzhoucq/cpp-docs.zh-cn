---
title: 项目生成错误 PRJ0030 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0030
dev_langs:
- C++
helpviewer_keywords:
- PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 964fedd40f577a8b337c4ad0c20ba80d33ed2a23
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099882"
---
# <a name="project-build-error-prj0030"></a>项目生成错误 PRJ0030

宏展开错误。 针对 $（宏） 计算超过 32 级。

宏中的递归导致此错误。 例如，如果您设置**中间目录**属性 (请参阅[常规属性页 （项目）](../../ide/general-property-page-project.md)) 为 $(IntDir)，您将得到递归。

若要解决此错误，未定义的宏或在宏用于定义方面的属性。