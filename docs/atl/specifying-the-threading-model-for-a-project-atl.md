---
title: 指定线程处理模型项目 (ATL) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- _ATL_FREE_THREADED macro
- _ATL_APARTMENT_THREADED macro
- ATL, multithreading
- threading [ATL], models
- _ATL_SINGLE_THREADED macro
ms.assetid: 6b571078-521c-4f3e-9f08-482aa235a822
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6f807aa82a62fb703430ace5bc6be516e08ca9dc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359631"
---
# <a name="specifying-the-threading-model-for-a-project-atl"></a>指定项目的线程模型 (ATL)
下列宏是可用于指定 ATL 项目的线程模型：  
  
|宏|使用指南|  
|-----------|--------------------------|  
|_ATL_SINGLE_THREADED|如果你的对象的所有使用单个线程处理模型中定义。|  
|_ATL_APARTMENT_THREADED|如果一个或多个对象使用单元线程处理中定义。|  
|_ATL_FREE_THREADED|如果一个或多个对象使用免费或非特定线程处理中定义。 现有的代码可能包含等效的宏的引用[_ATL_MULTI_THREADED](reference/compiler-options-macros.md#_atl_multi_threaded)。|  
  
 如果为你的项目未定义任何这些宏，_ATL_FREE_THREADED 将生效所示。  
  
 这些宏，如下所示影响运行时性能：  
  
-   指定的宏，对应于你的项目中的对象可以提高运行时性能。  
  
-   指定的宏，例如，如果时所有对象都是单线程，指定 _ATL_APARTMENT_THREADED 更高级别将略有降低运行时性能。  
  
-   如指定 _ATL_SINGLE_THREADED 时一个或多个对象使用单元线程处理或自由线程处理，请指定较低级别的宏，例如，可能会导致你的应用程序在运行时失败。  
  
 请参阅[选项，ATL 简单对象向导](../atl/reference/options-atl-simple-object-wizard.md)有关的说明的线程处理模型可用于 ATL 对象。  
  
## <a name="see-also"></a>请参阅  
 [概念](../atl/active-template-library-atl-concepts.md)

