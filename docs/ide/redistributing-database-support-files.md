---
title: 重新分发数据库支持文件 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- redistributing database support files
- database support files [C++], redistributing
ms.assetid: d80cffe0-177c-4515-9de7-fbf0517eb8d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a51697367480569e2d27a4cb67791f5fe4d39a8f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323870"
---
# <a name="redistributing-database-support-files"></a>重新分发数据库支持文件
可以重新发布用于数据访问对象 (DAO) 以及 Microsoft 数据访问 SDK 中数据库技术的支持文件。  
  
## <a name="installing-dao-support-files"></a>安装 DAO 支持文件  
 若要获取最新版本的 DAO，请参见 Microsoft 支持网站上的[文章 239114：如何获取 Microsoft Jet 4.0 数据库引擎的最新 Service Pack](http://go.microsoft.com/fwlink/p/?linkid=198014)。  
  
## <a name="installing-microsoft-data-access-sdk-support-files"></a>安装 Microsoft 数据访问 SDK 支持文件  
 使用 Mdac_typ.exe 安装 ODBC、OLE DB、ActiveX 数据对象 (ADO) 和 远程桌面服务 (RDS) 的支持文件。 Mdac_typ.exe 位于 Visual Studio 安装媒体上的 ..\WCU\MDAC28\ 文件夹中。 还可以从 [Microsoft 下载中心](http://go.microsoft.com/fwlink/p/?linkid=198015)网站下载 Mdac_typ.exe。  
  
 有关更多信息，请在 [MSDN](http://go.microsoft.com/fwlink/p/?linkid=198016) 网站上，搜索“重新分发 MDAC 2.8 SP1”。 如果使用 Visual Studio 安装项目部署应用程序，请参阅[部署和依赖项](http://msdn.microsoft.com/en-us/49e9b84d-bd6a-4388-b9ac-46ea79cf0733)。  
  
## <a name="see-also"></a>请参阅  
 [重新分发 Visual C++ 文件](../ide/redistributing-visual-cpp-files.md)