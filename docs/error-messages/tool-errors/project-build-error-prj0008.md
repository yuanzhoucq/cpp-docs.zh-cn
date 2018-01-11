---
title: "项目生成错误 PRJ0008 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0008
dev_langs: C++
helpviewer_keywords: PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1740b0cf1edfc90258de4fe26478298ddf2875c6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0008"></a>项目生成错误 PRJ0008
无法删除文件 file。  
  
 **请确保文件未被另一个进程打开，并且未被写保护。**  
  
 重新生成或清理期间，Visual c + + 删除所有已知中间文件和输出文件的生成，以及满足中的通配符规范的任何文件**删除的扩展**中的属性[常规配置设置属性页](../../ide/general-property-page-project.md)。  
  
 如果 Visual c + + 不能删除文件，你将看到此错误。 若要解决此错误，使该文件，并且其目录可写执行生成的用户。