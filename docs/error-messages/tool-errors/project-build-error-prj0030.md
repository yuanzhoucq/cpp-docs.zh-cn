---
title: 项目生成错误 PRJ0030
ms.date: 11/04/2016
f1_keywords:
- PRJ0030
helpviewer_keywords:
- PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
ms.openlocfilehash: aa1c8539247287f7644742857c3cb7de321a20a2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385389"
---
# <a name="project-build-error-prj0030"></a>项目生成错误 PRJ0030

宏展开错误。 针对 $（宏） 计算超过 32 级。

宏中的递归导致此错误。 例如，如果您设置**中间目录**属性 (请参阅[常规属性页 （项目）](../../build/reference/general-property-page-project.md)) 为 $(IntDir)，您将得到递归。

若要解决此错误，未定义的宏或在宏用于定义方面的属性。