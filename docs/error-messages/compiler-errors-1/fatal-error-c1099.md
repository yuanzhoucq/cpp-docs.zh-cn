---
title: "错误 C1099 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C1099
dev_langs: C++
helpviewer_keywords: C1099
ms.assetid: c050b074-a06a-4026-9e10-569029cc0739
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 928ced6fe9e283cf16db651ecbf6164164e3174e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1099"></a>错误 C1099
“编辑并继续”引擎正在终止编译  
  
 “编辑并继续”在准备进行编译代码更改的过程中加载了一个预编译头文件，但后续操作（例如预编译头 `#include` 语句前的代码更改或停止调试器）阻止“编辑并继续”使用该进程完成编译。 不需要执行任何操作来修复此错误。