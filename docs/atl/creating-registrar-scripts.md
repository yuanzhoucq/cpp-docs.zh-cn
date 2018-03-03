---
title: "创建 ATL 注册器脚本 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- scripting, registry scripting
- ATL, registry
- registrar scripts [ATL]
- scripts, Registrar scripts
- scripts, creating
ms.assetid: cbd5024b-8061-4a71-be65-7fee90374a35
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b3bda4043693d14451a2de14cbc71fbecdcdddba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="creating-registrar-scripts"></a>Creating Registrar Scripts
注册器脚本提供对系统注册表的数据驱动的而不是驱动 API 访问。 数据驱动的访问是通常更高效，因为它采用一个脚本来向注册表添加项只能将一个或两个行。  
  
 [ATL 控件向导](../atl/reference/atl-control-wizard.md)自动生成用于您的 COM 服务器的注册器脚本。 你可以在与你的对象关联的.rgs 文件中找到此脚本。  
  
 ATL 注册机构的脚本引擎处理在运行时的注册器脚本。 ATL 在服务器安装过程会自动调用脚本引擎。  
  
 本文介绍如何注册器脚本相关的以下主题：  
  
-   [了解巴科斯范式 (BNF) 语法](../atl/understanding-backus-nauer-form-bnf-syntax.md)  
  
-   [了解分析树](../atl/understanding-parse-trees.md)  
  
-   [注册表脚本示例](../atl/registry-scripting-examples.md)  
  
-   [使用可替换参数（注册器预处理器）](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)  
  
-   [调用脚本](../atl/invoking-scripts.md)  
  
## <a name="see-also"></a>请参阅  
 [注册表组件 （注册器）](../atl/atl-registry-component-registrar.md)

