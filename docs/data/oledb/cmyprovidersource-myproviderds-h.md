---
title: "CMyProviderSource (MyProviderDS.H) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- myproviderds.h
- cmyprovidersource
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderSource class in MyProviderDS.H
ms.assetid: c143d48e-59c8-4f67-9141-3aab51859b92
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8704a4a0733ea8bf688378953af9ff01314271d1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="cmyprovidersource-myproviderdsh"></a>CMyProviderSource (MyProviderDS.H)
提供程序类使用多重继承。 下面的代码演示数据源对象的继承链：  
  
```cpp
/////////////////////////////////////////////////////////////////////////  
// CMyProviderSource  
class ATL_NO_VTABLE CMyProviderSource :   
   public CComObjectRootEx<CComSingleThreadModel>,  
   public CComCoClass<CMyProviderSource, &CLSID_MyProvider>,  
   public IDBCreateSessionImpl<CMyProviderSource, CMyProviderSession>,  
   public IDBInitializeImpl<CMyProviderSource>,  
   public IDBPropertiesImpl<CMyProviderSource>,  
   public IPersistImpl<CMyProviderSource>,  
   public IInternalConnectionImpl<CMyProviderSource>  
```  
  
 所有 COM 组件均都派生自`CComObjectRootEx`和`CComCoClass`。 `CComObjectRootEx` 提供有关的所有实现**IUnknown**接口。 它可以处理任何线程处理模型。 `CComCoClass` 处理所需的任何错误支持。 如果你想要发送到客户端的更丰富的错误信息，则可以使用某些错误 Api 中`CComCoClass`。  
  
 从多个 Impl 类还继承数据源对象。 每个类提供接口的实现。 数据源对象实现`IPersist`， `IDBProperties`， **IDBInitialize**，和**IDBCreateSession**接口。 每个接口是实现所必需的 OLE DB 数据源对象。 你可以选择支持或通过继承或从这些 Impl 类之一不继承支持特定功能。 如果你想要支持**IDBDataSourceAdmin**从继承的接口， **IDBDataSourceAdminImpl**类，以获取所需的功能。  
  
## <a name="com-map"></a>COM 映射  
 每当客户端调用`QueryInterface`对于在数据源上的接口，它将经历以下 COM 映射：  
  
```  
BEGIN_COM_MAP(CMyProviderSource)  
   COM_INTERFACE_ENTRY(IDBCreateSession)  
   COM_INTERFACE_ENTRY(IDBInitialize)  
   COM_INTERFACE_ENTRY(IDBProperties)  
   COM_INTERFACE_ENTRY(IPersist)  
   COM_INTERFACE_ENTRY(IInternalConnection)  
END_COM_MAP()  
```  
  
 COM_INTERFACE_ENTRY 宏来自 ATL 和告诉的实现`QueryInterface`中`CComObjectRootEx`返回相应的接口。  
  
## <a name="property-map"></a>属性映射  
 属性映射指定了指定的提供程序的所有属性：  
  
```  
BEGIN_PROPSET_MAP(CMyProviderSource)  
   BEGIN_PROPERTY_SET(DBPROPSET_DATASOURCEINFO)  
      PROPERTY_INFO_ENTRY(ACTIVESESSIONS)  
      PROPERTY_INFO_ENTRY(ASYNCTXNABORT)  
      PROPERTY_INFO_ENTRY(ASYNCTXNCOMMIT)  
      PROPERTY_INFO_ENTRY(BYREFACCESSORS)  
      PROPERTY_INFO_ENTRY_VALUE(CATALOGLOCATION, DBPROPVAL_CL_START)  
      PROPERTY_INFO_ENTRY(CATALOGTERM)  
      PROPERTY_INFO_ENTRY(CATALOGUSAGE)  
      PROPERTY_INFO_ENTRY(COLUMNDEFINITION)  
      PROPERTY_INFO_ENTRY(CONCATNULLBEHAVIOR)  
      PROPERTY_INFO_ENTRY(DATASOURCENAME)  
      PROPERTY_INFO_ENTRY(DATASOURCEREADONLY)  
      PROPERTY_INFO_ENTRY(DBMSNAME)  
      PROPERTY_INFO_ENTRY(DBMSVER)  
      PROPERTY_INFO_ENTRY_VALUE(DSOTHREADMODEL, DBPROPVAL_RT_FREETHREAD)  
      PROPERTY_INFO_ENTRY(GROUPBY)  
      PROPERTY_INFO_ENTRY(HETEROGENEOUSTABLES)  
      PROPERTY_INFO_ENTRY(IDENTIFIERCASE)  
      PROPERTY_INFO_ENTRY(MAXINDEXSIZE)  
      PROPERTY_INFO_ENTRY(MAXROWSIZE)  
      PROPERTY_INFO_ENTRY(MAXROWSIZEINCLUDESBLOB)  
      PROPERTY_INFO_ENTRY(MAXTABLESINSELECT)  
      PROPERTY_INFO_ENTRY(MULTIPLEPARAMSETS)  
      PROPERTY_INFO_ENTRY(MULTIPLERESULTS)  
      PROPERTY_INFO_ENTRY(MULTIPLESTORAGEOBJECTS)  
      PROPERTY_INFO_ENTRY(MULTITABLEUPDATE)  
      PROPERTY_INFO_ENTRY(NULLCOLLATION)  
      PROPERTY_INFO_ENTRY(OLEOBJECTS)  
      PROPERTY_INFO_ENTRY(ORDERBYCOLUMNSINSELECT)  
      PROPERTY_INFO_ENTRY(OUTPUTPARAMETERAVAILABILITY)  
      PROPERTY_INFO_ENTRY(PERSISTENTIDTYPE)  
      PROPERTY_INFO_ENTRY(PREPAREABORTBEHAVIOR)  
      PROPERTY_INFO_ENTRY(PREPARECOMMITBEHAVIOR)  
      PROPERTY_INFO_ENTRY(PROCEDURETERM)  
      PROPERTY_INFO_ENTRY(PROVIDERNAME)  
      PROPERTY_INFO_ENTRY(PROVIDEROLEDBVER)  
      PROPERTY_INFO_ENTRY(PROVIDERVER)  
      PROPERTY_INFO_ENTRY(QUOTEDIDENTIFIERCASE)  
      PROPERTY_INFO_ENTRY(ROWSETCONVERSIONSONCOMMAND)  
      PROPERTY_INFO_ENTRY(SCHEMATERM)  
      PROPERTY_INFO_ENTRY(SCHEMAUSAGE)  
      PROPERTY_INFO_ENTRY(STRUCTUREDSTORAGE)  
      PROPERTY_INFO_ENTRY(SUBQUERIES)  
      PROPERTY_INFO_ENTRY(TABLETERM)  
      PROPERTY_INFO_ENTRY(USERNAME)  
   END_PROPERTY_SET(DBPROPSET_DATASOURCEINFO)  
   BEGIN_PROPERTY_SET(DBPROPSET_DBINIT)  
      PROPERTY_INFO_ENTRY(AUTH_PASSWORD)  
      PROPERTY_INFO_ENTRY(AUTH_PERSIST_SENSITIVE_AUTHINFO)  
      PROPERTY_INFO_ENTRY(AUTH_USERID)  
      PROPERTY_INFO_ENTRY(INIT_DATASOURCE)  
      PROPERTY_INFO_ENTRY(INIT_HWND)  
      PROPERTY_INFO_ENTRY(INIT_LCID)  
      PROPERTY_INFO_ENTRY(INIT_LOCATION)  
      PROPERTY_INFO_ENTRY(INIT_MODE)  
      PROPERTY_INFO_ENTRY(INIT_PROMPT)  
      PROPERTY_INFO_ENTRY(INIT_PROVIDERSTRING)  
      PROPERTY_INFO_ENTRY(INIT_TIMEOUT)  
   END_PROPERTY_SET(DBPROPSET_DBINIT)  
   BEGIN_PROPERTY_SET(DBPROPSET_DATASOURCE)  
      PROPERTY_INFO_ENTRY(CURRENTCATALOG)  
   END_PROPERTY_SET(DBPROPSET_DATASOURCE)  
   CHAIN_PROPERTY_SET(CMyProviderSession)  
END_PROPSET_MAP()  
```  
  
 OLE DB 中的属性进行分组。 数据源对象具有两个组的属性： 一个用于**DBPROPSET_DATASOURCEINFO**集，另一个用于**DBPROPSET_DBINIT**设置。 **DBPROPSET_DATASOURCEINFO**集对应于有关提供程序和其数据源的属性。 **DBPROPSET_DBINIT**集对应于用于在初始化属性。 OLE DB 提供程序模板处理这些集所包含的 PROPERTY_SET 宏。 这些宏创建包含属性的数组的块。 每当客户端调用`IDBProperties`界面，该提供程序使用的属性映射。  
  
 不需要实现规范中的每个属性。 但是，你必须支持所需的属性;请参阅详细信息级别 0 一致性规范。 如果您不想要支持的属性，你可以从映射中删除它。 如果你想要支持的属性，请使用 PROPERTY_INFO_ENTRY 宏将其脚本添加到映射中。 宏对应于**UPROPINFO**结构，如下面的代码中所示：  
  
```  
struct UPROPINFO  
{  
   DBPROPID    dwPropId;  
   ULONG       ulIDS;  
   VARTYPE     VarType;  
   DBPROPFLAGS dwFlags;  
   union  
   {  
      DWORD dwVal;  
      LPOLESTR szVal;  
   };  
   DBPROPOPTIONS dwOption;  
};  
```  
  
 结构中的每个元素表示要处理的属性的信息。 它包含**DBPROPID**来确定的 GUID 和 ID 属性。 它还包含项，以确定的类型和值的属性。  
  
 如果你想要更改的属性 （请注意，使用者可以随时更改可写属性的值） 的默认值，你可以使用 PROPERTY_INFO_ENTRY_VALUE 或 PROPERTY_INFO_ENTRY_EX 宏。 这些宏，可以指定对应的属性的值。 PROPERTY_INFO_ENTRY_VALUE 宏是允许你更改的值的速记表示法。 PROPERTY_INFO_ENTRY_VALUE 宏将调用 PROPERTY_INFO_ENTRY_EX 宏。 此宏，可添加或更改中的属性的所有**UPROPINFO**结构。  
  
 如果你想要定义您自己的属性集，你可以添加一个通过使其他 BEGIN_PROPSET_MAP/END_PROPSET_MAP 组合。 你需要定义属性集的 GUID，然后定义您自己的属性。 如果你有提供程序特定属性，则将它们添加到新的属性，而不是使用一个现有设置。 这样就避免了更高版本的 OLE DB 中的问题。  
  
## <a name="user-defined-property-sets"></a>用户定义的属性集  
 Visual c + + 支持用户定义的属性集。 无需重写**GetProperties**或`GetPropertyInfo`。 相反，模板检测到任何用户定义的属性集，并将其添加到适当的对象。  
  
 如果你有需要在初始化时保持可用的用户定义的属性集 (即，使用者调用之前**idbinitialize:: Initialize**)，则可以通过指定此**UPROPSET_USERINIT**结合 BEGIN_PROPERTY_SET_EX 宏的标志。 属性集必须在这种方式 （如 OLE DB 规范要求） 的数据源对象。 例如:  
  
```  
BEGIN_PROPERTY_SET_EX(DBPROPSET_MYPROPSET, UPROPSET_USERINIT)  
   PROPERTY_INFO_ENTRY(DBPROP_MYPROP)  
END_PROPERTY_SET_EX(DBPROPSET_MYPROPSET)  
```  
  
## <a name="see-also"></a>请参阅  
 [提供程序向导生成的文件](../../data/oledb/provider-wizard-generated-files.md)