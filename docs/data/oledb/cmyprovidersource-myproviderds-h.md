---
title: "CMyProviderSource (MyProviderDS.H) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - ""myproviderds.h""
  - "cmyprovidersource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MyProviderDS.H 中的 CMyProviderSource 类"
  - "OLE DB 提供程序, 向导生成的文件"
ms.assetid: c143d48e-59c8-4f67-9141-3aab51859b92
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMyProviderSource (MyProviderDS.H)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此提供程序类使用多重继承。  以下代码显示数据源对象的继承链：  
  
```  
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
  
 所有 COM 组件均派生自 `CComObjectRootEx` 和 `CComCoClass`。  `CComObjectRootEx` 提供 **IUnknown** 接口的所有实现。  它可以处理任何线程模型。  `CComCoClass` 处理任何所需的错误支持。  如果要向客户端发送更丰富的错误信息，可以使用 `CComCoClass` 中的一些错误 API。  
  
 数据源对象也从若干“Impl”类继承。  每个类都提供了接口实现。  数据源对象实现 `IPersist`、`IDBProperties`、**IDBInitialize** 和 **IDBCreateSession** 接口。  OLE DB 必须用每个接口来实现数据源对象。  通过从这些“Impl”类之一继承或不继承，可以选择支持或不支持特定功能。  如果要支持 **IDBDataSourceAdmin** 接口，则从 **IDBDataSourceAdminImpl** 类继承以获取必需的功能。  
  
## COM 映射  
 每当客户端对数据源上的接口调用 `QueryInterface` 时，它都经过如下 COM 映射：  
  
```  
BEGIN_COM_MAP(CMyProviderSource)  
   COM_INTERFACE_ENTRY(IDBCreateSession)  
   COM_INTERFACE_ENTRY(IDBInitialize)  
   COM_INTERFACE_ENTRY(IDBProperties)  
   COM_INTERFACE_ENTRY(IPersist)  
   COM_INTERFACE_ENTRY(IInternalConnection)  
END_COM_MAP()  
```  
  
 COM\_INTERFACE\_ENTRY 宏来自 ATL，它通知 `CComObjectRootEx` 中的 `QueryInterface` 实现返回适当的接口。  
  
## 属性映射  
 属性映射指定提供程序指定的所有属性：  
  
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
  
 OLE DB 中的属性是分组的。  数据源对象有两组属性：一组用于 **DBPROPSET\_DATASOURCEINFO** 集；一组用于 **DBPROPSET\_DBINIT** 集。  **DBPROPSET\_DATASOURCEINFO** 集对应于有关提供程序及其数据源的属性。  **DBPROPSET\_DBINIT** 集对应于初始化时使用的属性。  OLE DB 提供程序模板用 PROPERTY\_SET 宏处理这些集。  这些宏创建包含属性数组的块。  每当客户端调用 `IDBProperties` 接口时，提供程序都使用属性映射。  
  
 不需要实现规范中的每个属性。  但是必须支持必需的属性；有关更多信息，请参见级别 0 一致性规范。  如果不希望支持某个属性，可以将其从映射中移除。  如果希望支持某个属性，使用 PROPERTY\_INFO\_ENTRY 宏将其添加到映射中。  宏对应于如下代码中显示的 **UPROPINFO** 结构：  
  
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
  
 结构中的每个元素表示处理属性的信息。  它包含确定属性的 GUID 和 ID 的 **DBPROPID**。  还包含确定属性的类型和值的项。  
  
 如果要更改属性的默认值（注意使用者可以随时更改可写属性的值），可以使用 PROPERTY\_INFO\_ENTRY\_VALUE 宏或 PROPERTY\_INFO\_ENTRY\_EX 宏。  这些宏允许指定相应属性的值。  PROPERTY\_INFO\_ENTRY\_VALUE 宏是允许更改值的速记法。  PROPERTY\_INFO\_ENTRY\_VALUE 宏调用 PROPERTY\_INFO\_ENTRY\_EX 宏。  此宏允许添加或更改 **UPROPINFO** 结构中的所有特性。  
  
 如果要定义自己的属性集，可以通过进行附加的 BEGIN\_PROPSET\_MAP\/END\_PROPSET\_MAP 组合来添加一个。  需要定义属性集的 GUID，然后定义自己的属性。  如果有提供程序特定的属性，将它们添加到新属性集而不是使用现有的属性集。  这样可以避免 OLE DB 更高版本中的问题。  
  
## 用户定义的属性集  
 Visual C\+\+ .NET 支持用户定义的属性集。  再不必重写 **GetProperties** 或 `GetPropertyInfo`。  相反，模板将检测到任何用户定义的属性集并将其添加到适当的对象中。  
  
 如果用户定义的属性集需要在初始化时（即在使用者调用 **IDBInitialize::Initialize** 之前）可用，可以通过与 BEGIN\_PROPERTY\_SET\_EX 宏一起使用 **UPROPSET\_USERINIT** 标志来指定此操作。  属性集必须在数据源对象中，此操作才有效（OLE DB 规范要求这样做）。  例如：  
  
```  
BEGIN_PROPERTY_SET_EX(DBPROPSET_MYPROPSET, UPROPSET_USERINIT)  
   PROPERTY_INFO_ENTRY(DBPROP_MYPROP)  
END_PROPERTY_SET_EX(DBPROPSET_MYPROPSET)  
```  
  
## 请参阅  
 [提供程序向导生成的文件](../../data/oledb/provider-wizard-generated-files.md)