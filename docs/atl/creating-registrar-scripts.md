---
title: 为 ATL 注册器创建脚本
ms.date: 05/14/2014
helpviewer_keywords:
- scripting, registry scripting
- ATL, registry
- registrar scripts [ATL]
- scripts, Registrar scripts
- scripts, creating
ms.assetid: cbd5024b-8061-4a71-be65-7fee90374a35
ms.openlocfilehash: f32606701ea08736985f0b0dd2ed82712040a049
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707062"
---
# <a name="creating-registrar-scripts"></a>创建注册器脚本

注册器脚本提供对系统注册表的数据驱动的访问，而非 API 驱动的访问。 数据驱动的访问通常更有效，因为它只需使用脚本中的一两行即可向注册表添加项。

[ATL 控件向导](../atl/reference/atl-control-wizard.md)会自动为你的 COM 服务器生成注册器脚本。 可以在与你的对象关联的 .rgs 文件中找到此脚本。

ATL 注册器的脚本引擎会在运行时处理你的注册器脚本。 ATL 会在服务器设置期间自动调用脚本引擎。

本文介绍了与注册器脚本相关的以下主题：

- [了解巴科斯-诺尔范式 (BNF) 语法](../atl/understanding-backus-naur-form-bnf-syntax.md)

- [了解分析树](../atl/understanding-parse-trees.md)

- [注册表脚本示例](../atl/registry-scripting-examples.md)

- [使用可替换参数（注册器预处理器）](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)

- [调用脚本](../atl/invoking-scripts.md)

## <a name="see-also"></a>请参阅

[注册表组件（注册器）](../atl/atl-registry-component-registrar.md)
