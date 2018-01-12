---
title: "项目生成错误 PRJ0030 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0030
dev_langs: C++
helpviewer_keywords: PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b6fe537dd8e6705fd5e30929a2480eb1d9ef9119
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0030"></a>项目生成错误 PRJ0030
宏扩展时出错。 （宏） 评估超过 32 级。  
  
 通过在宏中的递归导致此错误。 例如，如果你设置**中间目录**属性 (请参阅[常规属性页 （项目）](../../ide/general-property-page-project.md)) 为 $(IntDir)，您将得到递归。  
  
 若要解决此错误，未定义宏或在它们用于定义的宏方面的属性。