---
title: 创建 ATL 注册器脚本
ms.date: 11/04/2016
helpviewer_keywords:
- scripting, registry scripting
- ATL, registry
- registrar scripts [ATL]
- scripts, Registrar scripts
- scripts, creating
ms.assetid: cbd5024b-8061-4a71-be65-7fee90374a35
ms.openlocfilehash: e1a0b66e673fcefd0b75683ef75247a388217361
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62250837"
---
# <a name="creating-registrar-scripts"></a>Creating Registrar Scripts

注册器脚本提供数据驱动的而不是 API 驱动，访问系统注册表。 数据驱动的访问是通常效率更高，因为它需要向注册表添加项的脚本中只能将一个或两个行。

[ATL 控件向导](../atl/reference/atl-control-wizard.md)自动生成您的 COM 服务器的注册器脚本。 可以在与您的对象关联的.rgs 文件中找到此脚本。

ATL 注册器脚本引擎在运行时处理注册器脚本。 ATL server 安装过程会自动调用脚本引擎。

本文介绍如何注册器脚本与相关的以下主题：

- [了解巴科斯范式 (BNF) 语法](../atl/understanding-backus-nauer-form-bnf-syntax.md)

- [了解分析树](../atl/understanding-parse-trees.md)

- [注册表脚本示例](../atl/registry-scripting-examples.md)

- [使用可替换参数（注册器预处理器）](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)

- [调用脚本](../atl/invoking-scripts.md)

## <a name="see-also"></a>请参阅

[注册表组件 （注册器）](../atl/atl-registry-component-registrar.md)
