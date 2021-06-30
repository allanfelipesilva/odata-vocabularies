# EnterpriseSearch Vocabulary
**Namespace: [com.sap.vocabularies.EnterpriseSearch.v1](EnterpriseSearch.xml)**

Terms for Enterprise Search


## Terms

Term|Type|Description
:---|:---|:----------
[enabled](EnterpriseSearch.xml#L36)|Boolean|<a name="enabled"></a>Has to be true. The view has to be defined as @Search.searchable and needs a valid anchor key definition.
[hidden](EnterpriseSearch.xml#L40)|Boolean|<a name="hidden"></a>If set to true, the view is not part of the default search scope of a federated search that is used if no SCOPE parameter is given in a search call. In other words, the view is not searched if the view name is not explicitly given in the SCOPE parameter. If this annotation is not given, the default value is 'false' and the view is part of the default search scope.
[key](EnterpriseSearch.xml#L44)|Boolean|<a name="key"></a>Defines a column that is part of the anchor key<br>All anchor key columns have to be part of the same database table and this has to be the first (i.e., the leftmost) table that is used in the view definition. The anchor key columns have to define a unique key of the anchor table. Usually the anchor key columns are identical to the primary key columns of the anchor table. In this case, a client column, annotated with @EnterpriseSearch.client set to true, can be omitted from the anchor key definition.
[searchOptions](EnterpriseSearch.xml#L49)|String|<a name="searchOptions"></a>Defines the search options string that is passed to the CONTAINS() predicate when searching in the column.
[defaultValueSuggestElement](EnterpriseSearch.xml#L52)|Boolean|<a name="defaultValueSuggestElement"></a>Defines a column that is used to calculate suggestions
[fieldGroupForSearchQuery](EnterpriseSearch.xml#L55)|\[[FieldGroupForSearchQueryType](#FieldGroupForSearchQueryType)\]|<a name="fieldGroupForSearchQuery"></a>Defines the ranking weight for a column
[filteringFacet](EnterpriseSearch.xml#L68)|[FilteringFacetType](#FilteringFacetType)|<a name="filteringFacet"></a>Defines a filtering facet
[filteringAttribute](EnterpriseSearch.xml#L132)|[FilteringAttributeType](#FilteringAttributeType)|<a name="filteringAttribute"></a>Defines a filtering attribute
[snippets](EnterpriseSearch.xml#L155)|[SnippetsType](#SnippetsType)|<a name="snippets"></a>Defines snippets
[highlighted](EnterpriseSearch.xml#L177)|[HighlightedType](#HighlightedType)|<a name="highlighted"></a>Defines highlithing behavior

## <a name="FieldGroupForSearchQueryType"></a>[FieldGroupForSearchQueryType](EnterpriseSearch.xml#L58)


Property|Type|Description
:-------|:---|:----------
[name](EnterpriseSearch.xml#L59)|String|Defines the name of a field group. The name is used in the query language as a reference to the field group.
[elements](EnterpriseSearch.xml#L62)|\[String\]|Contains a list of column names. This defines the view columns that belong to the field group.

## <a name="FilteringFacetType"></a>[FilteringFacetType](EnterpriseSearch.xml#L71)


Property|Type|Description
:-------|:---|:----------
[default](EnterpriseSearch.xml#L72)|Boolean|Defines a column as a facet column<br>If set to true, a facet is automatically returned for this column in the search response if facets are enabled (with custom query option facets=all, for example). If set to false, a facet for this column is returned only if the facet is requested explicitly (by adding the column name to custom query option facets as, for example, facets=AMOUNT,INSTITUTIONCOUNTRY). If the annotation @EnterpriseSearch.filteringFacet.default is not given but any of the other filteringFacet annotations is used for a column, this implicitly also sets @EnterpriseSearch.filteringFacet.default to false. Beginning with Enterprise Search version 5, columns of CDS type hana.ST_POINT can also be defined as facet columns.
[displayPosition](EnterpriseSearch.xml#L79)|Int16|Defines the sequence of facet columns in the search response.<br>If the number of facets returned in the search response is limited to n (by setting the facets option to n, as, for example, facets=3), only the first n facets in the order defined by the display position are returned. The use of this annotation is optional. But as soon as it is used in a view defini-tion, it has to be given for all facet columns. All facet columns of a leveled hierarchy have to be assigned to the same display position. For all other facet columns the display position has to be unique. If the displayPosition annotation is not used, facet columns are returned in a stable order so that consecutive calls to sys.esh_search() return the same sequence of facet columns.
[numberOfValues](EnterpriseSearch.xml#L86)|Int16|Defines the number of values that are returned in the facet. If this parameter is not given, 10 values are returned by default.
[order](EnterpriseSearch.xml#L89)|[OrderType](#OrderType)|Defines the sorting for facet columns.
[caseInsensitiveAggregation](EnterpriseSearch.xml#L92)|Boolean|If set to true, a case-insensitive aggregation of facet values is done. If not given or set to false, the default aggregation is case-sensitive.
[countNullValues](EnterpriseSearch.xml#L95)|Boolean|If set to true, facets also return an anchor object count for NULL values. If not given or set to false, NULL values are not returned.NULL values are returned only for facets that show single values. If intervals are returned (for date, numeric or spatial SQL types), NULL values are not part of the facet.
[noIntervals](EnterpriseSearch.xml#L98)|Boolean|If set to true, date facets and numeric facets are returned as single values instead of intervals.If set to false, date facets and numeric facets are returned as intervals. This is the default behavior.

## <a name="OrderType"></a>[OrderType](EnterpriseSearch.xml#L102)


Property|Type|Description
:-------|:---|:----------
[by](EnterpriseSearch.xml#L103)|[byType](#byType)|Defines the sort criterion for facet columns.<br>The annotation cannot be used for spatial datatypes (hana.ST_POINT, hana.ST_GEOMETRY), as these cannot be sorted.
[byReference](EnterpriseSearch.xml#L107)|String|Defines the name of a column that is used as a sort criterion for a facet column.<br>The facet is sorted by the contents of the column that is referenced by this annotation. For example, a facet that counts documents for month names can be sorted by the month number so that the UI displays the month names in the right sequence. In this case, the month name is defined as a facet column and this annotation references the view column that contains the number of the month. The referenced column cannot be defined as a language-dependent column.
[direction](EnterpriseSearch.xml#L113)|[directionType](#directionType)|Defines whether the facet is sorted in an ascending or descending order.<br>The default is in a descending order for a facet that is sorted by NUMBER_OF_HITS. In all other cases, the default is to sort in an ascending order.

## <a name="directionType"></a>[directionType](EnterpriseSearch.xml#L119)


Member|Value|Description
:-----|----:|:----------
[ASC](EnterpriseSearch.xml#L120)|0|
[DESC](EnterpriseSearch.xml#L121)|1|

## <a name="byType"></a>[byType](EnterpriseSearch.xml#L123)


Member|Value|Description
:-----|----:|:----------
[NUMBER_OF_HITS](EnterpriseSearch.xml#L124)|0|If set to NUMBER_OF_HITS, the facet is sorted by the number of distinct anchor objects belonging to each facet value. This is the default behavior.
[FILTER_ELEMENT_VALUE](EnterpriseSearch.xml#L127)|1|If set to FILTER_ELEMENT_VALUE, the facet is sorted by the value of the facet column.

## <a name="FilteringAttributeType"></a>[FilteringAttributeType](EnterpriseSearch.xml#L135)


Property|Type|Description
:-------|:---|:----------
[default](EnterpriseSearch.xml#L136)|Boolean|filteringAttribute annotations can be used by search UIs to identify elements that are suitable for filter conditions but that shall usually not be displayed as facets.<br>If needed by the UI, elements with filteringAttribute annotations can be explicitly requested as facets. To get the facet values, the element name has to be explicitly added to the facets option of the search call. If facets are requested with facets=all or facets=n (with n > 0), columns with filteringAttribute annotations are never returned.
[displayPosition](EnterpriseSearch.xml#L141)|Int16|Defines the sequence of facet columns in the search response.<br>Only if the element is explicitly requested as a facet column. See @EnterpriseSearch.filteringFacet.displayPosition for details.
[caseInsensitiveAggregation](EnterpriseSearch.xml#L146)|Boolean|If set to true, a case-insensitive aggregation of facet values is done. If not given or set to false, the default aggregation is case-sensitive. Only if the element is explicitly requested as a facet column.
[countNullValues](EnterpriseSearch.xml#L149)|Boolean|Defines a column that is used to calculate suggestions, if set to true.

## <a name="SnippetsType"></a>[SnippetsType](EnterpriseSearch.xml#L158)


Property|Type|Description
:-------|:---|:----------
[enabled](EnterpriseSearch.xml#L159)|Boolean|Enables snippet calculation for a column.<br>Only snippets for columns with a presentation mode other than 'NONE' will be returned in the search result. The original column content is not returned if snippets are enabled. In other words, either a snippet or a column value are returned in the search result. The column has to support text search. This means it needs a fulltext index or has to be of SQL type TEXT, BINTEXT or SHORTTEXT.Note This annotation must not be used for columns that are part of a 1:n join. Beginning with API version 4, this annotation is also allowed for columns that are part of a 1:n join if these columns are defined as multi-values or subobjects. For sys.esh_search() calls up to API version 20302 (/v20303/$all?...), snippets are always returned for all columns that have a snippets annotation, independent of presentation mode annotations. If a column has a presentation mode annotation, both the original column value and the snippet are returned in the search response.
[maximumLength ](EnterpriseSearch.xml#L167)|Int16|Defines the maximum length of a snippet in characters.<br>For columns with annotation @EnterpriseSearch.snippets.enabled set to true this annotation defines the maximum length of a snippet that is returned in the search response. The annotation also defines the maximum length of a snippet that is returned as part of the whyfound information. If the whyfound information contains a highlighted text, the maximum length parameter is ignored. The snippet returned will be as long as possible but it will never be longer than the given maximum length. Without this annotation a snippet has a maximum length of 5000 characters but the length of the snippet depends on the number of different tokens that are found in the column.

## <a name="HighlightedType"></a>[HighlightedType](EnterpriseSearch.xml#L180)


Property|Type|Description
:-------|:---|:----------
[enabled](EnterpriseSearch.xml#L181)|Boolean|Enables highlighting for a column.<br>Only highlighting for columns with a presentation mode other than 'NONE' will be returned in the search result. The original column content is not returned if highlighting is enabled. In other words, either a highlighted text or a column value are returned in the search results. It is possible to get both snippets and highlighted text in the search result by setting both annotations. The column has to support text search. This means it needs a fulltext index or has to be of SQL type TEXT, BINTEXT or SHORTTEXT. Beginning with API version 4, this annotation is also allowed for columns that are part of a 1:n join if these columns are defined as multi-values or subobjects. For sys.esh_search() calls up to API version 20302 (/v20303/$all?...), highlighted text is always returned for all columns that have a highlighted annotation, independent of presentation mode annotations. If a column has a presentation mode annotation, both the original column value and the highlighted text are returned in the search response.
