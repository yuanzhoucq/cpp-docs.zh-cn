---
title: "资源编译器错误 RC1015 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: RC1015
dev_langs: C++
helpviewer_keywords: RC1015
ms.assetid: 23f187e1-5538-40b5-9042-edd2888f55c2
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 666221cf5c3e812cd856271ea97cf4966383ec20
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-fatal-error-rc1015"></a>资源编译器错误 RC1015
无法打开包含文件 filename  
  
 给定的包含文件不存在、 无法打开或找不到。  
  
 确保环境设置有效，并且已为该文件指定了正确的路径。 确保足够的文件句柄可供资源编译器。 如果此文件位于网络驱动器，请确保您有权打开该文件。  
  
 在“配置属性”->“资源”->“常规”属性页中可配置“附加包含目录”，即使包含文件存在于该“附加包含目录”所指定的目录中，也可能发生 RC1015；请指定包含文件的完整路径。  
  
 有关详细信息，请参阅知识库文章 Q326987: RC1015 错误时使用资源视图 Include 路径是否太长。