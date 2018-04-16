---
title: "错误 C1854 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1854
dev_langs:
- C++
helpviewer_keywords:
- C1854
ms.assetid: 8c21a9cc-1737-475c-9e57-8725cd8937c1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0e0a26e902b1a40203bb4323bce8e28e687e9647
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1854"></a>错误 C1854
  
> 无法覆盖创建对象文件中的预编译标头的过程中形成的信息:*filename*  
  
你指定[/Yu （使用预编译标头文件）](../../build/reference/yu-use-precompiled-header-file.md)选项后指定[/Yc （创建预编译标头文件）](../../build/reference/yc-create-precompiled-header-file.md)相同的文件的选项。  
  
若要解决此问题，通常情况下，只有一个文件在项目中设置你要通过使用编译**/Yc**选项，然后将所有其他文件来通过编译设置**/Yu**选项。 有关详细信息的使用**/Yc**选项，以及如何在 Visual Studio IDE 中设置它，请参阅[/Yc （创建预编译标头文件）](../../build/reference/yc-create-precompiled-header-file.md)。 有关如何使用预编译标头的详细信息，请参阅[创建预编译标头文件](../../build/reference/creating-precompiled-header-files.md)。  
