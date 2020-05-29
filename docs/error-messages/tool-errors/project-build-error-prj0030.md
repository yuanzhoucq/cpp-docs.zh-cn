---
title: 项目生成错误 PRJ0030
ms.date: 11/04/2016
f1_keywords:
- PRJ0030
helpviewer_keywords:
- PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
ms.openlocfilehash: 3675c3796ae37df848e458aa2db665d8c4aa7766
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192505"
---
# <a name="project-build-error-prj0030"></a>项目生成错误 PRJ0030

宏扩展错误。 为 $ （宏）评估超过32级别的递归。

此错误是由宏中的递归导致的。 例如，如果将**中间目录**属性（请参阅 "[常规属性页（项目）](../../build/reference/general-property-page-project.md)"）设置为 $ （IntDir），则会获得递归。

若要解决此错误，请不要使用宏或属性来定义它们。
