---
title: "项目生成错误 PRJ0006 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0006
dev_langs: C++
helpviewer_keywords: PRJ0006
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ef1dff813c709a117d92abcdd7a2d4f9d3420c65
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="project-build-error-prj0006"></a>项目生成错误 PRJ0006
无法打开临时文件 file。 请确保文件存在，而且，目录未写入-受保护。  
  
 Visual c + + 无法在生成过程中创建临时文件。 其中的原因包括：  
  
-   没有临时目录。  
  
-   只读的临时目录。  
  
-   磁盘空间不足。  
  
-   $ （intdir） 文件夹是只读的或包含临时文件的是只读的。  
  
 此错误也会出现以下错误 PRJ0007： 无法创建输出目录目录。 错误 PRJ0007 意味着无法创建的 $ （intdir） 目录，并暗示临时文件的创建也将失败。  
  
 只要你指定就会创建临时文件：  
  
-   响应文件。  
  
-   自定义生成步骤。  
  
-   生成事件。