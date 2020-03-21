---
title: CCustomSource (CustomDS.H)
ms.date: 10/22/2018
f1_keywords:
- myproviderds.h
- cmyprovidersource
- customds.h
- ccustomsource
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderSource class in MyProviderDS.H
- CCustomSource class in CustomDS.H
ms.assetid: c143d48e-59c8-4f67-9141-3aab51859b92
ms.openlocfilehash: 60324ae914c9490144a715e06323ee6d184ce201
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079725"
---
# <a name="ccustomsource-customdsh"></a>CCustomSource （CustomDS）

提供程序类使用多重继承。 下面的代码显示了数据源对象的继承链：

```cpp
/////////////////////////////////////////////////////////////////////////
// CCustomSource
class ATL_NO_VTABLE CCustomSource :
   public CComObjectRootEx<CComSingleThreadModel>,
   public CComCoClass<CCustomSource, &CLSID_Custom>,
   public IDBCreateSessionImpl<CCustomSource, CCustomSession>,
   public IDBInitializeImpl<CCustomSource>,
   public IDBPropertiesImpl<CCustomSource>,
   public IPersistImpl<CCustomSource>,
   public IInternalConnectionImpl<CCustomSource>
```

所有 COM 组件都从 `CComObjectRootEx` 和 `CComCoClass`派生。 `CComObjectRootEx` 提供 `IUnknown` 接口的所有实现。 它可以处理任何线程模型。 `CComCoClass` 处理所需的任何错误支持。 如果要将更丰富的错误信息发送到客户端，可以使用 `CComCoClass`中的一些错误 Api。

数据源对象还继承自多个 "Impl" 类。 每个类都提供接口的实现。 数据源对象实现 `IPersist`、`IDBProperties`、`IDBInitialize`和 `IDBCreateSession` 接口。 OLE DB 实现数据源对象需要每个接口。 您可以通过继承或不继承其中一个 "Impl" 类来选择支持或不支持特定功能。 如果要支持 `IDBDataSourceAdmin` 接口，请从 `IDBDataSourceAdminImpl` 类继承，以获取所需功能。

## <a name="com-map"></a>COM 映射

每当客户端为数据源上的接口调用 `QueryInterface` 时，它都会经历以下 COM 映射：

```cpp
/////////////////////////////////////////////////////////////////////////
// CCustomSource
class ATL_NO_VTABLE CCustomSource :
   public CComObjectRootEx<CComSingleThreadModel>,
   public CComCoClass<CCustomSource, &CLSID_Custom>,
   public IDBCreateSessionImpl<CCustomSource, CCustomSession>,
   public IDBInitializeImpl<CCustomSource>,
   public IDBPropertiesImpl<CCustomSource>,
   public IPersistImpl<CCustomSource>,
   public IInternalConnectionImpl<CCustomSource>
```

所有 COM 组件都从 `CComObjectRootEx` 和 `CComCoClass`派生。 `CComObjectRootEx` 提供 `IUnknown` 接口的所有实现。 它可以处理任何线程模型。 `CComCoClass` 处理所需的任何错误支持。 如果要将更丰富的错误信息发送到客户端，可以使用 `CComCoClass`中的一些错误 Api。

数据源对象还继承自多个 "Impl" 类。 每个类都提供接口的实现。 数据源对象实现 `IPersist`、`IDBProperties`、`IDBInitialize`和 `IDBCreateSession` 接口。 OLE DB 实现数据源对象需要每个接口。 您可以通过继承或不继承其中一个 "Impl" 类来选择支持或不支持特定功能。 如果要支持 `IDBDataSourceAdmin` 接口，请从 `IDBDataSourceAdminImpl` 类继承，以获取所需功能。

## <a name="com-map"></a>COM 映射

每当客户端为数据源上的接口调用 `QueryInterface` 时，它都会经历以下 COM 映射：

```cpp
BEGIN_COM_MAP(CCustomSource)
   COM_INTERFACE_ENTRY(IDBCreateSession)
   COM_INTERFACE_ENTRY(IDBInitialize)
   COM_INTERFACE_ENTRY(IDBProperties)
   COM_INTERFACE_ENTRY(IPersist)
   COM_INTERFACE_ENTRY(IInternalConnection)
END_COM_MAP()
```

COM_INTERFACE_ENTRY 的宏来自 ATL，并通知 `CComObjectRootEx` 中 `QueryInterface` 的实现返回相应的接口。

## <a name="property-map"></a>属性映射

属性映射指定提供程序分配的所有属性：

```cpp
BEGIN_PROPSET_MAP(CCustomSource)
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
   CHAIN_PROPERTY_SET(CCustomSession)
END_PROPSET_MAP()
```

OLE DB 中的属性进行分组。 数据源对象具有两组属性：一个用于 DBPROPSET_DATASOURCEINFO 集，一个用于 DBPROPSET_DBINIT 集。 DBPROPSET_DATASOURCEINFO 集对应于提供程序及其数据源的属性。 DBPROPSET_DBINIT 集对应于初始化时使用的属性。 OLE DB 提供程序模板用 PROPERTY_SET 宏来处理这些集。 宏创建包含属性数组的块。 只要客户端调用 `IDBProperties` 接口，提供程序就会使用属性映射。

不需要在规范中实现每个属性。 但是，必须支持所需的属性;有关详细信息，请参阅 level 0 一致性规范。 如果不想支持某个属性，则可以将其从映射中删除。 如果要支持某个属性，请使用 PROPERTY_INFO_ENTRY 宏将其添加到地图中。 宏对应于 `UPROPINFO` 结构，如以下代码所示：

```cpp
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

结构中的每个元素都表示用于处理属性的信息。 它包含用于确定属性的 GUID 和 ID 的 `DBPROPID`。 它还包含用于确定属性的类型和值的条目。

如果要更改属性的默认值（请注意，使用者随时可以更改可写属性的值），则可以使用 PROPERTY_INFO_ENTRY_VALUE 或 PROPERTY_INFO_ENTRY_EX 宏。 这些宏允许您为相应的属性指定一个值。 PROPERTY_INFO_ENTRY_VALUE 宏是一种简略表示法，可用于更改值。 PROPERTY_INFO_ENTRY_VALUE 宏调用 PROPERTY_INFO_ENTRY_EX 的宏。 此宏可用于添加或更改 `UPROPINFO` 结构中的所有属性。

如果要定义自己的属性集，可以通过额外的 BEGIN_PROPSET_MAP/END_PROPSET_MAP 组合来添加一个属性集。 为属性集定义 GUID，然后定义自己的属性。 如果有特定于提供程序的属性，请将它们添加到新的属性集，而不是使用现有的属性集。 这可以避免在 OLE DB 的更高版本中出现问题。

## <a name="user-defined-property-sets"></a>用户定义的属性集

视觉C++对象支持用户定义的属性集。 无需覆盖 `GetProperties` 或 `GetPropertyInfo`。 相反，模板会检测任何用户定义的属性集，并将其添加到适当的对象。

如果用户定义属性集需要在初始化时可用（即，在使用者调用 `IDBInitialize::Initialize`之前），则可以通过使用 UPROPSET_USERINIT 标志和 BEGIN_PROPERTY_SET_EX 宏来指定此属性。 属性集必须在数据源对象中才能正常运行（如 OLE DB 规范所要求）。 例如：

```cpp
BEGIN_PROPERTY_SET_EX(DBPROPSET_MYPROPSET, UPROPSET_USERINIT)
   PROPERTY_INFO_ENTRY(DBPROP_MYPROP)
END_PROPERTY_SET_EX(DBPROPSET_MYPROPSET)
```

## <a name="see-also"></a>另请参阅

[提供程序向导生成的文件](../../data/oledb/provider-wizard-generated-files.md)<br/>
