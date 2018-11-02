---
title: 指定项目的线程模型 (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- _ATL_FREE_THREADED macro
- _ATL_APARTMENT_THREADED macro
- ATL, multithreading
- threading [ATL], models
- _ATL_SINGLE_THREADED macro
ms.assetid: 6b571078-521c-4f3e-9f08-482aa235a822
ms.openlocfilehash: 419c9880573c2058b3bb60b9c77e4f3ca065fab7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569879"
---
# <a name="specifying-the-threading-model-for-a-project-atl"></a>指定项目的线程模型 (ATL)

下列宏是可用于指定 ATL 项目的线程模型：

|宏|使用准则|
|-----------|--------------------------|
|_ATL_SINGLE_THREADED|如果所有对象都使用单线程模型中，定义。|
|_ATL_APARTMENT_THREADED|如果一个或多个对象使用单元线程处理，定义。|
|_ATL_FREE_THREADED|如果一个或多个对象使用免费的还是中立线程，定义。 现有代码可能包含引用等效宏[_ATL_MULTI_THREADED](reference/compiler-options-macros.md#_atl_multi_threaded)。|

如果为你的项目未定义任何这些宏，_ATL_FREE_THREADED 将生效。

宏会影响运行时性能，如下所示：

- 指定的宏，对应于你的项目中的对象可以提高运行时性能。

- 指定更高级别的宏，例如，如果您指定 _ATL_APARTMENT_THREADED 时所有对象都是单线程，将会略微降低运行时性能。

- 指定较低级别的宏，例如，如果指定 _ATL_SINGLE_THREADED 时一个或多个对象使用单元线程处理或自由线程处理可能导致应用程序在运行时失败。

请参阅[选项，ATL 简单对象向导](../atl/reference/options-atl-simple-object-wizard.md)有关线程处理的说明可用于 ATL 对象进行建模。

## <a name="see-also"></a>请参阅

[概念](../atl/active-template-library-atl-concepts.md)

