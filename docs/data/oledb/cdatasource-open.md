---
title: "Cdatasource:: Open |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CDataSource::Open
- ATL.CDataSource.Open
- CDataSource::Open
- CDataSource.Open
dev_langs: C++
helpviewer_keywords: Open method
ms.assetid: a6d28bd1-799a-48ed-8993-5f82d1705b77
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3f2215b84600e2691f6b3aeb0407c5c6b96ebd00
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cdatasourceopen"></a>CDataSource::Open
打开与数据源使用的连接**CLSID**， **ProgID**，或`CEnumerator`名字对象或通过一个定位器对话框提示用户。  
  
## <a name="syntax"></a>语法  
  
```  
  
      HRESULT Open(  
   const CLSID& clsid,  
   DBPROPSET* pPropSet = NULL,  
   ULONG nPropertySets = 1   
) throw( );  
HRESULT Open(  
   const CLSID& clsid,  
   LPCTSTR pName,  
   LPCTSTR pUserName = NULL,  
   LPCTSTR pPassword = NULL,  
   long nInitMode = 0   
) throw( );  
HRESULT Open(  
   LPCTSTR szProgID,  
   DBPROPSET* pPropSet = NULL,  
   ULONG nPropertySets = 1   
) throw( );  
HRESULT Open(  
   LPCTSTR szProgID,  
   LPCTSTR pName,  
   LPCTSTR pUserName = NULL,  
   LPCTSTR pPassword = NULL,  
   long nInitMode = 0   
) throw( );  
HRESULT Open(  
   const CEnumerator& enumerator,  
   DBPROPSET* pPropSet = NULL,  
   ULONG nPropertySets = 1   
) throw( );  
HRESULT Open(  
   const CEnumerator& enumerator,  
   LPCTSTR pName,  
   LPCTSTR pUserName = NULL,  
   LPCTSTR pPassword = NULL,  
   long nInitMode = 0   
) throw( );  
HRESULT Open(  
   HWND hWnd = GetActiveWindow( ),  
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_WIZARDSHEET   
) throw( );  
HRESULT Open(   
   LPCWSTR szProgID,   
   DBPROPSET* pPropSet = NULL,   
   ULONG nPropertySets = 1   
) throw( );  
HRESULT Open(   
   LPCSTR szProgID,   
   LPCTSTR pName,   
   LPCTSTR pUserName = NULL,   
   LPCTSTR pPassword = NULL,   
   long nInitMode = 0   
) throw( );  
```  
  
#### <a name="parameters"></a>参数  
 `clsid`  
 [in]**CLSID**数据提供程序。  
  
 *pPropSet*  
 [in]指向数组的指针[DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx)包含属性和要设置值的结构。 请参阅[属性设置和属性组](https://msdn.microsoft.com/en-us/library/ms713696.aspx)中*OLE DB 程序员参考*Windows SDK 中。  
  
 *nPropertySets*  
 [in]数[DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx)结构*pPropSet*自变量。  
  
 *pName*  
 [in] 要连接的数据库的名称。  
  
 *pUserName*  
 [in] 用户的名称。  
  
 *pPassword*  
 [in] 用户的密码。  
  
 `nInitMode`  
 [in] 数据库初始化模式。 请参阅[初始化属性](https://msdn.microsoft.com/en-us/library/ms723127.aspx)中*OLE DB 程序员参考*Windows SDK for 有效初始化模式的列表中。 如果 `nInitMode` 是零，则用于打开连接的属性集中不包含初始化模式。  
  
 `szProgID`  
 [in] 一个程序标识符。  
  
 `enumerator`  
 [in]A [CEnumerator](../../data/oledb/cenumerator-class.md)用于获取调用方未指定时打开连接的名字对象的对象**CLSID**。  
  
 `hWnd`  
 [in] 将成为对话框父级的窗口的句柄。 使用函数重载（该函数重载使用 `hWnd` 参数）将自动调用服务组件；请参见备注了解详细信息。  
  
 `dwPromptOptions`  
 [in] 确定要显示的定位器对话框的样式。 请参阅 Msdasc.h 了解可能的值。  
  
## <a name="return-value"></a>返回值  
 一个标准 `HRESULT`。  
  
## <a name="remarks"></a>备注  
 使用 `hWnd` 参数的方法重载使用 oledb32.dll 中的服务组件打开数据源对象；此 DLL 包含资源池、自动事务登记等服务组件功能的实现。 有关详细信息，请参阅"OLE DB 服务"上的 OLE DB 程序员参考中[http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true)。  
  
 不使用 `hWnd` 参数的方法重载无需使用 oledb32.dll 中的服务组件即可打开数据源对象。 A [CDataSource](../../data/oledb/cdatasource-class.md)使用这些函数重载打开的对象将无法利用任何服务组件的功能。  
  
## <a name="example"></a>示例  
 下面的代码演示如何使用 OLE DB 模板打开 Jet 4.0 数据源。 你将 Jet 数据源视为 OLE DB 数据源。 但是，你调用**打开**需要两个属性集： 一个用于**DBPROPSET_DBINIT** ，另一个用于**DBPROPSET_JETOLEDB_DBINIT**，以便可以设置**DBPROP_JETOLEDB_DATABASEPASSWORD**。  
  
 [!code-cpp[NVC_OLEDB_Consumer#7](../../data/oledb/codesnippet/cpp/cdatasource-open_1.cpp)]  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDataSource 类](../../data/oledb/cdatasource-class.md)