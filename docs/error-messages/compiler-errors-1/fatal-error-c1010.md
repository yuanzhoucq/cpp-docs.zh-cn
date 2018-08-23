---
title: 错误 C1010 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1010
dev_langs:
- C++
helpviewer_keywords:
- C1010
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf8af35b28cfa02bd2723ff3c78db04a27cc39ba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198490"
---
# <a name="fatal-error-c1010"></a>错误 C1010
查找预编译头时意外的文件尾。 是否忘记添加 #include 名称对源？  
  
 使用指定的包含文件[/Yu](../../build/reference/yu-use-precompiled-header-file.md)源文件中未列出。  默认情况下，在大多数 Visual c + + 项目类型中启用了此选项，并且"stdafx.h"默认值包括此选项指定的文件。  
  
 在 Visual Studio 环境中，使用以下方法之一来解决此错误：  
  
-   如果你的项目中不使用预编译标头，设置**创建/使用预编译标头**属性源文件复制到**不使用预编译头**。 若要设置此编译器选项，请按照下列步骤：  
  
    1.  在项目的解决方案资源管理器窗格中，右键单击项目名称，然后单击**属性**。  
  
    2.  在左窗格中，单击**C/c + +** 文件夹。  
  
    3.  单击**预编译标头**节点。  
  
    4.  在右窗格中，单击**创建/使用预编译标头**，然后单击**不使用预编译头**。  
  
-   请确保不要意外删除、 重命名或删除了标头文件 (默认情况下，stdafx.h) 从当前项目。 此文件还需要在你使用的源文件中的任何其他代码之前包含 **#include"stdafx.h"**。 (此标头文件指定为**通过文件创建/使用 PCH**项目属性)