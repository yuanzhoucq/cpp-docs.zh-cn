---
title: 项目生成错误 PRJ0030 |Microsoft 文档
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
ms.openlocfilehash: 1bf1c9137f8c4ed0d80955eef38b07ea86204a5c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33317653"
---
# <a name="project-build-error-prj0030"></a>项目生成错误 PRJ0030
宏扩展时出错。 （宏） 评估超过 32 级。  
  
 通过在宏中的递归导致此错误。 例如，如果你设置**中间目录**属性 (请参阅[常规属性页 （项目）](../../ide/general-property-page-project.md)) 为 $(IntDir)，您将得到递归。  
  
 若要解决此错误，未定义宏或在它们用于定义的宏方面的属性。