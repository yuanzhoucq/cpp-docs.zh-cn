---
title: 项目生成错误 PRJ0030
ms.date: 11/04/2016
f1_keywords:
- PRJ0030
helpviewer_keywords:
- PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
ms.openlocfilehash: 2a6cde4ca48acb9aadfe3109084483dbb554e1e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488070"
---
# <a name="project-build-error-prj0030"></a>项目生成错误 PRJ0030

宏展开错误。 针对 $（宏） 计算超过 32 级。

宏中的递归导致此错误。 例如，如果您设置**中间目录**属性 (请参阅[常规属性页 （项目）](../../ide/general-property-page-project.md)) 为 $(IntDir)，您将得到递归。

若要解决此错误，未定义的宏或在宏用于定义方面的属性。