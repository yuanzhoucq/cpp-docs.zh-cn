---
title: "pgosweep |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- pgosweep program
- profile-guided optimizations, pgosweep
ms.assetid: f39dd3b7-1cd9-4c3b-8e8b-fb794744b757
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 78ae6c36011e3c10359988cf2c501514d1bcf70a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="pgosweep"></a>pgosweep
使用按配置优化以从正在运行的程序的所有配置文件数据写入到对应的.pgc 文件。  
  
## <a name="syntax"></a>语法  
  
```  
pgosweep [options] image pgcfile  
```  
  
#### <a name="parameters"></a>参数  
 `options`  
 可选参数，可以为空。 有效值`options`如下所示：  
  
-   **/?** 或**/help，**显示帮助消息。  
  
-   **/noreset，**保留的运行时数据结构中的计数。  
  
 `image`  
 通过使用编译器选项 /ltcg: pginstrument 会创建的.exe 或.dll 文件的完整路径。  
  
 `pgcfile`  
 此命令将在其中写出数据计数.pgc 文件。  
  
## <a name="remarks"></a>备注  
 此命令适用于使用 /ltcg: pginstrument 编译器选项生成的程序。 中断正在运行的程序，并将配置文件数据写入新的.pgc 文件。 默认情况下，该命令将在每个写入操作后重置计数。 如果指定**/noreset**选项，该命令将记录的值，但不是会重置它们正在运行的程序。 检索配置文件数据更高版本，此选项将为你提供的重复数据。  
  
 其他用途`pgosweep`是检索只是为了运行时的应用程序的配置文件信息。 例如，可以运行`pgosweep`后很快启动应用程序并丢弃该文件。 这将删除与启动成本关联的配置文件数据。 然后，可以运行`pgosweep`结束应用程序之前。 现在所收集的数据具有只能从运行时的配置文件信息。  
  
 当名称对应的.pgc 文件 (`pgcfile`) 可以使用标准的格式，这是*appname ！ n*.pgc。 如果你使用此格式，则编译器将在 /ltcg: pgo 阶段中找到此数据。 如果不使用标准的格式，则必须使用[pgomgr](../../build/reference/pgomgr.md)以合并.pgc 文件。  
  
## <a name="example"></a>示例  
  
```  
pgosweep myapp.exe myapp!1.pgc  
```  
  
 在此示例中，`pgosweep`写入 myapp!1.pgc myapp.exe 的当前配置文件信息。  
  
## <a name="see-also"></a>请参阅  
 [用于按配置文件手动优化的工具](../../build/reference/tools-for-manual-profile-guided-optimization.md)