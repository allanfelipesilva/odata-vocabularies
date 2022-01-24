# Search Vocabulary
**Namespace: [com.sap.vocabularies.Search.v1](Search.xml)**

Terms for Search


## Terms

Term|Type|Description
:---|:---|:----------
[searchable](Search.xml#L36)|Boolean|<a name="searchable"></a>Defines if a CDS view or entity is generally relevant for search scenarios.<br>The annotation offers a general switch and a means to quickly detect whether a view is relevant or not. Set to true to enable @Search annotations. At least one column has to be defined as defaultSearchElement.
[defaultSearchElement](Search.xml#L41)|Boolean|<a name="defaultSearchElement"></a>Defines a column as full-text search column.<br>At least one column has to be defined as default full-text search column. Search in views without default full-text search elements is not supported.
[ranking](Search.xml#L46)|[RankingEnumType](#RankingEnumType)|<a name="ranking"></a>Defines the ranking weight for a column
[fuzinessThreshold](Search.xml#L60)|Decimal|<a name="fuzinessThreshold"></a>Defines the threshold for a fuzzy search.<br>Default value is 1. This means that an exact search is performed.
[termMappingDictionary](Search.xml#L65)|String|<a name="termMappingDictionary"></a>Defines the name of the term mapping table.<br>Defines the name of the term mapping table (format: schemaname.tablename). passed to the search option 'termMappingTable' of the CONTAINS() predicate.
[termMappingListID](Search.xml#L69)|\[String\]|<a name="termMappingListID"></a>Defines the names of the term mapping list IDs.<br>Defines the names of the term mapping list IDs, passed to the search option 'termMappingListId' of the CONTAINS() predicate.
[fulltextIndex](Search.xml#L73)|Boolean|<a name="fulltextIndex"></a>If set to true, a configuration fails if there is no full-text index defined for the element.

## <a name="RankingEnumType"></a>[RankingEnumType](Search.xml#L49)


Member|Value|Description
:-----|----:|:----------
[HIGH](Search.xml#L50)|1|The HIGH ranking weights 1.0
[MEDIUM](Search.xml#L53)|0.7|The MEDIUM ranking weights 0.7
[LOW](Search.xml#L56)|0.5|The LOW ranking weights 0.5
