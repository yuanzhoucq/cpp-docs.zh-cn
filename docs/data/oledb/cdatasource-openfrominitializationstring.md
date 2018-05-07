---
title: 'Cdatasource:: Openfrominitializationstring |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDataSource.OpenFromInitializationString
- OpenFromInitializationString
- CDataSource::OpenFromInitializationString
- ATL::CDataSource::OpenFromInitializationString
- ATL.CDataSource.OpenFromInitializationString
dev_langs:
- C++
helpviewer_keywords:
- OpenFromInitializationString method
ms.assetid: 5ef1f1fd-92a9-4e1c-ad80-d3601b094b8c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dac964f7c6c863f85769a164fab8c418e1c45430
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cdatasourceopenfrominitializationstring"></a>CDataSource::OpenFromInitializationString
打开用户提供的初始化字符串指定数据源。  
  
## <a name="syntax"></a>语法  
  
```
HRESULT OpenFromInitializationString(LPCOLESTR szInitializationString,   
   bool fPromptForInfo= false) throw();  
```  
  
#### <a name="parameters"></a>参数  
 *szInitializationString*  
 [in]初始化字符串中。  
  
 *fPromptForInfo*  
 [in]如果此参数设置为**true**，然后`OpenFromInitializationString`将设置**DBPROP_INIT_PROMPT**属性**DBPROMPT_COMPLETEREQUIRED**，它指定用户是系统提示仅在需要时的详细信息。 这对于在其中初始化字符串指定需要密码，数据库的情况下很有用，但字符串不包含密码。 将提示用户输入密码 （或其他任何缺少的信息） 尝试连接到数据库时。  
  
 默认值是**false**，它指定永远不会提示用户 (设置**DBPROP_INIT_PROMPT**到**DBPROMPT_NOPROMPT**)。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 此方法使用 oledb32.dll 中的服务组件打开数据源对象；此 DLL 包含资源池、自动事务登记等服务组件功能的实现。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDataSource 类](../../data/oledb/cdatasource-class.md)