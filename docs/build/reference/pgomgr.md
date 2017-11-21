---
title: "pgomgr |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- pgomgr program
- profile-guided optimizations, pgomgr
ms.assetid: 74589126-df18-42c9-8739-26d60e148d6a
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ab078acd8aaadef19659ad766233ea191b360e02
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="pgomgr"></a>pgomgr
将配置文件数据从一个或多个对应的.pgc 文件添加到该.pgd 文件。  
  
## <a name="syntax"></a>语法  
  
```  
pgomgr [options] pgcfiles pgdfile  
```  
  
#### <a name="parameters"></a>参数  
 `options`  
 到 pgomgr，可以指定以下选项：  
  
 **/help-**显示可用 pgomgr 选项 (短，无法用于 /？)。  
  
 **/ 清除-**导致要清除的所有配置文件信息的.pgd 文件。 不能指定.pgc 文件时**/清除**指定。  
  
 **详细介绍/**-显示详细统计信息，包括流 graph 覆盖率信息。  
  
 **/ 摘要**— 显示每个函数统计信息。  
  
 **/ 唯一**-一起使用时**/摘要**，原因修饰函数名以显示。  默认值，当 / 唯一是未使用，为要显示的未修饰的函数名称。  
  
 **/merge**[**:***n*]**-**导致中或多个对应的.pgc 文件添加到该.pgd 文件的数据。  可选参数，  *n* ，允许你指定应添加 hat 数据 *n* 时间。  例如，如果一个方案通常将执行 6 次，你可以在测试运行中一次执行并将其添加.pgd 文件六倍**pgomgr /merge:6**。  
  
 `pgcfiles`  
 一个或多个.pgc 文件，你想要合并到.pgd 文件的配置文件数据。 你可以指定单个对应的.pgc 文件或多个对应的.pgc 文件。 如果未指定任何对应的.pgc 文件，pgomgr 将合并所有对应的.pgc 文件的文件名同名的.pgd 文件。  
  
 `pgdfile`  
 正在向其中合并来自的.pgc 文件或文件的数据使用.pgd 文件。  
  
## <a name="remarks"></a>备注  
  
> [!NOTE]
>  你只能从 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 命令提示符启动此工具。 不能从系统命令提示符或从文件资源管理器启动此工具。  
  
## <a name="example"></a>示例  
 在下面的示例中，使用.pgd 文件已清除的配置文件数据。  
  
```  
pgomgr /clear myapp.pgd  
```  
  
 在以下示例中，myapp1.pgc 中的配置文件数据已添加到该.pgd 文件 3 次。  
  
```  
pgomgr /merge:3 myapp1.pgc myapp.pgd  
```  
  
 在下面的示例中，从所有 myapp #.pgc 文件的配置文件数据添加到 myapp.pgd 文件。  
  
```  
pgomgr -merge myapp1.pgd  
```  
  
## <a name="see-also"></a>另请参阅  
 [用于按配置文件手动优化的工具](../../build/reference/tools-for-manual-profile-guided-optimization.md)