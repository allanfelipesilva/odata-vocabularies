# EnterpriseSearchHana Vocabulary
**Namespace: [com.sap.vocabularies.EnterpriseSearchHana.v1](Search.xml)**

Terms for Enterprise Search Hana


## Terms

Term|Type|Description
:---|:---|:----------
[searchable](Search.xml#L36)|Boolean|<a name="searchable"></a>Defines if a CDS view or entity is generally relevant for search scenarios.<p>The annotation offers a general switch and a means to quickly detect whether a view is relevant or not. Set to true to enable @Search annotations. At least one column has to be defined as defaultSearchElement.</p>
[defaultSearchElement](Search.xml#L41)|Boolean|<a name="defaultSearchElement"></a>Defines a column as full-text search column.<p>At least one column has to be defined as default full-text search column. Search in views without default full-text search elements is not supported.</p>
[ranking](Search.xml#L46)|[RankingEnumType](#RankingEnumType)|<a name="ranking"></a>Defines the ranking weight for a column
[fuzinessThreshold](Search.xml#L61)|Decimal|<a name="fuzinessThreshold"></a>Defines the threshold for a fuzzy search.<p>Default value is 1. This means that an exact search is performed.</p>
[termMappingDictionary](Search.xml#L66)|String|<a name="termMappingDictionary"></a>Defines the name of the term mapping table.<p>Defines the name of the term mapping table (format: schemaname.tablename). passed to the search option 'termMappingTable' of the CONTAINS() predicate.</p>
[termMappingListID](Search.xml#L70)|\[String\]|<a name="termMappingListID"></a>Defines the names of the term mapping list IDs.<p>Defines the names of the term mapping list IDs, passed to the search option 'termMappingListId' of the CONTAINS() predicate.</p>
[fulltextIndex](Search.xml#L74)|Boolean|<a name="fulltextIndex"></a>If set to true, a configuration fails if there is no full-text index defined for the element.
[enabled](Search.xml#L101)|Boolean|<a name="enabled"></a>Has to be true. The view has to be defined as @Search.searchable and needs a valid anchor key definition.
[hidden](Search.xml#L105)|Boolean|<a name="hidden"></a>If set to true, the view is not part of the default search scope of a federated search that is used if no SCOPE parameter is given in a search call. In other words, the view is not searched if the view name is not explicitly given in the SCOPE parameter. If this annotation is not given, the default value is 'false' and the view is part of the default search scope.
[key](Search.xml#L109)|Boolean|<a name="key"></a>Defines a column that is part of the anchor key<p>All anchor key columns have to be part of the same database table and this has to be the first (i.e., the leftmost) table that is used in the view definition. The anchor key columns have to define a unique key of the anchor table. Usually the anchor key columns are identical to the primary key columns of the anchor table. In this case, a client column, annotated with @EnterpriseSearch.client set to true, can be omitted from the anchor key definition.</p>
[searchOptions](Search.xml#L114)|String|<a name="searchOptions"></a>Defines the search options string that is passed to the CONTAINS() predicate when searching in the column.
[defaultValueSuggestElement](Search.xml#L117)|Boolean|<a name="defaultValueSuggestElement"></a>Defines a column that is used to calculate suggestions
[fieldGroupForSearchQuery](Search.xml#L120)|\[[FieldGroupForSearchQueryType](#FieldGroupForSearchQueryType)\]|<a name="fieldGroupForSearchQuery"></a>Defines the ranking weight for a column
[filteringFacet](Search.xml#L133)|[FilteringFacetType](#FilteringFacetType)|<a name="filteringFacet"></a>Defines a filtering facet
[filteringAttribute](Search.xml#L197)|[FilteringAttributeType](#FilteringAttributeType)|<a name="filteringAttribute"></a>Defines a filtering attribute
[snippets](Search.xml#L220)|[SnippetsType](#SnippetsType)|<a name="snippets"></a>Defines snippets
[highlighted](Search.xml#L242)|[HighlightedType](#HighlightedType)|<a name="highlighted"></a>Defines highlithing behavior
[arbitraryCardinality](Search.xml#L279)|Boolean|<a name="arbitraryCardinality"></a>Defines a column as a multi-value column.<p>This means that the column comes from an 1:n join and that it is returned in the search result as an array. This annotation is only allowed for columns that are of a SQL type that can be used in a group by clause.</p>
[weight](Search.xml#L284)|Decimal|<a name="weight"></a>Defines the ranking weight of a column that is used to calculate the overall score.<p>Only one of the annotations @EnterpriseSearchHana.weight and @Search.ranking can be used for a column.</p>
[identifier](Search.xml#L288)|String|<a name="identifier"></a>Defines the OData identifier of a column. The value has to be a valid OData identifier.<p>If an identifier is defined, the identifier is used instead of the original column name in all interfaces of esh_search() including the metadata call. In other words, the internal column name is not visible to the users of esh_search(). If this annotation is not given, the column name is used as an identifier.</p>
[numc](Search.xml#L292)|Boolean|<a name="numc"></a>Defines a column as an ABAP NUMC column (a numeric value padded with leading zeros).<p>Without score functions, a search in a NUMC column is done similar to an alphanum search limited to numeric characters.Interval facets are returned, if a facet is requested for a NUMC column.</p>
[layoutStructuredObject](Search.xml#L297)|[LayoutStructuredObjectType](#LayoutStructuredObjectType)|<a name="layoutStructuredObject"></a>Defines a subobject of the anchor object<p>This means that the columns of the subobject come from a 1:n join and are returned in the search result as an array.</p>
[uiResource](Search.xml#L337)|[UiResourceType](#UiResourceType)|<a name="uiResource"></a>
[translation](Search.xml#L350)|\[[TranslationType](#TranslationType)\]|<a name="translation"></a>Defines multilingual UI text directly in the search configuration as an alternative to resource bundles. The texts are returned in the output of a metadata call.
[navigation](Search.xml#L365)|[NavigationType](#NavigationType)|<a name="navigation"></a>
[boosting](Search.xml#L384)|[BoostingType](#BoostingType)|<a name="boosting"></a>

## <a name="RankingEnumType"></a>[RankingEnumType](Search.xml#L50)


Member|Value|Description
:-----|----:|:----------
[HIGH](Search.xml#L51)|1|The HIGH ranking weights 1.0
[MEDIUM](Search.xml#L54)|0.7|The MEDIUM ranking weights 0.7
[LOW](Search.xml#L57)|0.5|The LOW ranking weights 0.5

## <a name="FieldGroupForSearchQueryType"></a>[FieldGroupForSearchQueryType](Search.xml#L123)


Property|Type|Description
:-------|:---|:----------
[name](Search.xml#L124)|String|Defines the name of a field group. The name is used in the query language as a reference to the field group.
[elements](Search.xml#L127)|\[String\]|Contains a list of column names. This defines the view columns that belong to the field group.

## <a name="FilteringFacetType"></a>[FilteringFacetType](Search.xml#L136)


Property|Type|Description
:-------|:---|:----------
[default](Search.xml#L137)|Boolean|Defines a column as a facet column<p>If set to true, a facet is automatically returned for this column in the search response if facets are enabled (with custom query option facets=all, for example). If set to false, a facet for this column is returned only if the facet is requested explicitly (by adding the column name to custom query option facets as, for example, facets=AMOUNT,INSTITUTIONCOUNTRY). If the annotation @EnterpriseSearch.filteringFacet.default is not given but any of the other filteringFacet annotations is used for a column, this implicitly also sets @EnterpriseSearch.filteringFacet.default to false. Beginning with Enterprise Search version 5, columns of CDS type hana.ST_POINT can also be defined as facet columns.</p>
[displayPosition](Search.xml#L144)|Int16|Defines the sequence of facet columns in the search response.<p>If the number of facets returned in the search response is limited to n (by setting the facets option to n, as, for example, facets=3), only the first n facets in the order defined by the display position are returned. The use of this annotation is optional. But as soon as it is used in a view defini-tion, it has to be given for all facet columns. All facet columns of a leveled hierarchy have to be assigned to the same display position. For all other facet columns the display position has to be unique. If the displayPosition annotation is not used, facet columns are returned in a stable order so that consecutive calls to sys.esh_search() return the same sequence of facet columns.</p>
[numberOfValues](Search.xml#L151)|Int16|Defines the number of values that are returned in the facet. If this parameter is not given, 10 values are returned by default.
[order](Search.xml#L154)|[OrderType](#OrderType)|Defines the sorting for facet columns.
[caseInsensitiveAggregation](Search.xml#L157)|Boolean|If set to true, a case-insensitive aggregation of facet values is done. If not given or set to false, the default aggregation is case-sensitive.
[countNullValues](Search.xml#L160)|Boolean|If set to true, facets also return an anchor object count for NULL values. If not given or set to false, NULL values are not returned.NULL values are returned only for facets that show single values. If intervals are returned (for date, numeric or spatial SQL types), NULL values are not part of the facet.
[noIntervals](Search.xml#L163)|Boolean|If set to true, date facets and numeric facets are returned as single values instead of intervals.If set to false, date facets and numeric facets are returned as intervals. This is the default behavior.

## <a name="OrderType"></a>[OrderType](Search.xml#L167)


Property|Type|Description
:-------|:---|:----------
[by](Search.xml#L168)|[byType](#byType)|Defines the sort criterion for facet columns.<p>The annotation cannot be used for spatial datatypes (hana.ST_POINT, hana.ST_GEOMETRY), as these cannot be sorted.</p>
[byReference](Search.xml#L172)|String|Defines the name of a column that is used as a sort criterion for a facet column.<p>The facet is sorted by the contents of the column that is referenced by this annotation. For example, a facet that counts documents for month names can be sorted by the month number so that the UI displays the month names in the right sequence. In this case, the month name is defined as a facet column and this annotation references the view column that contains the number of the month. The referenced column cannot be defined as a language-dependent column.</p>
[direction](Search.xml#L178)|[directionType](#directionType)|Defines whether the facet is sorted in an ascending or descending order.<p>The default is in a descending order for a facet that is sorted by NUMBER_OF_HITS. In all other cases, the default is to sort in an ascending order.</p>

## <a name="directionType"></a>[directionType](Search.xml#L184)


Member|Value|Description
:-----|----:|:----------
[ASC](Search.xml#L185)|0|
[DESC](Search.xml#L186)|1|

## <a name="byType"></a>[byType](Search.xml#L188)


Member|Value|Description
:-----|----:|:----------
[NUMBER_OF_HITS](Search.xml#L189)|0|If set to NUMBER_OF_HITS, the facet is sorted by the number of distinct anchor objects belonging to each facet value. This is the default behavior.
[FILTER_ELEMENT_VALUE](Search.xml#L192)|1|If set to FILTER_ELEMENT_VALUE, the facet is sorted by the value of the facet column.

## <a name="FilteringAttributeType"></a>[FilteringAttributeType](Search.xml#L200)


Property|Type|Description
:-------|:---|:----------
[default](Search.xml#L201)|Boolean|filteringAttribute annotations can be used by search UIs to identify elements that are suitable for filter conditions but that shall usually not be displayed as facets.<p>If needed by the UI, elements with filteringAttribute annotations can be explicitly requested as facets. To get the facet values, the element name has to be explicitly added to the facets option of the search call. If facets are requested with facets=all or facets=n (with n > 0), columns with filteringAttribute annotations are never returned.</p>
[displayPosition](Search.xml#L206)|Int16|Defines the sequence of facet columns in the search response.<p>Only if the element is explicitly requested as a facet column. See @EnterpriseSearch.filteringFacet.displayPosition for details.</p>
[caseInsensitiveAggregation](Search.xml#L211)|Boolean|If set to true, a case-insensitive aggregation of facet values is done. If not given or set to false, the default aggregation is case-sensitive. Only if the element is explicitly requested as a facet column.
[countNullValues](Search.xml#L214)|Boolean|Defines a column that is used to calculate suggestions, if set to true.

## <a name="SnippetsType"></a>[SnippetsType](Search.xml#L223)


Property|Type|Description
:-------|:---|:----------
[enabled](Search.xml#L224)|Boolean|Enables snippet calculation for a column.<p>Only snippets for columns with a presentation mode other than 'NONE' will be returned in the search result. The original column content is not returned if snippets are enabled. In other words, either a snippet or a column value are returned in the search result. The column has to support text search. This means it needs a fulltext index or has to be of SQL type TEXT, BINTEXT or SHORTTEXT.Note This annotation must not be used for columns that are part of a 1:n join. Beginning with API version 4, this annotation is also allowed for columns that are part of a 1:n join if these columns are defined as multi-values or subobjects. For sys.esh_search() calls up to API version 20302 (/v20303/$all?...), snippets are always returned for all columns that have a snippets annotation, independent of presentation mode annotations. If a column has a presentation mode annotation, both the original column value and the snippet are returned in the search response.</p>
[maximumLength ](Search.xml#L232)|Int16|Defines the maximum length of a snippet in characters.<p>For columns with annotation @EnterpriseSearch.snippets.enabled set to true this annotation defines the maximum length of a snippet that is returned in the search response. The annotation also defines the maximum length of a snippet that is returned as part of the whyfound information. If the whyfound information contains a highlighted text, the maximum length parameter is ignored. The snippet returned will be as long as possible but it will never be longer than the given maximum length. Without this annotation a snippet has a maximum length of 5000 characters but the length of the snippet depends on the number of different tokens that are found in the column.</p>

## <a name="HighlightedType"></a>[HighlightedType](Search.xml#L245)


Property|Type|Description
:-------|:---|:----------
[enabled](Search.xml#L246)|Boolean|Enables highlighting for a column.<p>Only highlighting for columns with a presentation mode other than 'NONE' will be returned in the search result. The original column content is not returned if highlighting is enabled. In other words, either a highlighted text or a column value are returned in the search results. It is possible to get both snippets and highlighted text in the search result by setting both annotations. The column has to support text search. This means it needs a fulltext index or has to be of SQL type TEXT, BINTEXT or SHORTTEXT. Beginning with API version 4, this annotation is also allowed for columns that are part of a 1:n join if these columns are defined as multi-values or subobjects. For sys.esh_search() calls up to API version 20302 (/v20303/$all?...), highlighted text is always returned for all columns that have a highlighted annotation, independent of presentation mode annotations. If a column has a presentation mode annotation, both the original column value and the highlighted text are returned in the search response.</p>

## <a name="LayoutStructuredObjectType"></a>[LayoutStructuredObjectType](Search.xml#L301)


Property|Type|Description
:-------|:---|:----------
[arbitraryCardinality](Search.xml#L302)|Boolean|defines that the subobject comes from a 1:n join and that there may be multiple subobject instances for a given anchor object.
[layerId](Search.xml#L306)|String|Defines the name of the subobject.
[childIds](Search.xml#L309)|\[String\]|Defines the names of other subobjects that are included within the subobject.
[defaultExpand](Search.xml#L312)|[DefaultExpandType](#DefaultExpandType)|defines which subobjects are returned in the search result.
[elementList](Search.xml#L315)|\[[ElementListType](#ElementListType)\]|Defines the view columns that belong to the subobject.

## <a name="DefaultExpandType"></a>[DefaultExpandType](Search.xml#L319)


Member|Value|Description
:-----|----:|:----------
[WHY_FOUND](Search.xml#L320)|0|Only the subobject of the anchor object are returned that contain at least one of the search terms.
[ALL](Search.xml#L323)|1|All subobjects of an anchor object are returned.

## <a name="ElementListType"></a>[ElementListType](Search.xml#L327)


Property|Type|Description
:-------|:---|:----------
[element](Search.xml#L328)|String|Contains the name of a view column that belongs to the subobject.
[key](Search.xml#L331)|Boolean|Defines if a column is part of the subobject's key. Used to identify the distinct subobjects of an anchor object.<p>If there are no key columns defined for a subobject, all columns are used to identify the distinct subobjects.</p>

## <a name="UiResourceType"></a>[UiResourceType](Search.xml#L338)


Property|Type|Description
:-------|:---|:----------
[label](Search.xml#L339)|[UiResourceLabelType](#UiResourceLabelType)|

## <a name="UiResourceLabelType"></a>[UiResourceLabelType](Search.xml#L341)


Property|Type|Description
:-------|:---|:----------
[bundle](Search.xml#L342)|Boolean|Defines the name of a resource bundle. Can be used by the search ui to load a view label.
[key](Search.xml#L345)|String|defines the name of a key in a resource bundle. Can be used by the search ui to load a view label.

## <a name="TranslationType"></a>[TranslationType](Search.xml#L353)
Placeholder that is later used in the search configuration to reference the translated texts.

Property|Type|Description
:-------|:---|:----------
[id](Search.xml#L354)|String|
[value](Search.xml#L356)|\[[TranslationValueType](#TranslationValueType)\]|

## <a name="TranslationValueType"></a>[TranslationValueType](Search.xml#L358)


Property|Type|Description
:-------|:---|:----------
[language](Search.xml#L359)|String|Language code with location, IE: en_GB, en_US, en_AU, de_DE, de_AT.
[text](Search.xml#L362)|String|

## <a name="NavigationType"></a>[NavigationType](Search.xml#L366)


Property|Type|Description
:-------|:---|:----------
[panel](Search.xml#L367)|\[[NavigationPanelType](#NavigationPanelType)\]|
[attachByPosition](Search.xml#L368)|\[[TranslationAttachByPositionType](#TranslationAttachByPositionType)\]|
[attachToTitle](Search.xml#L369)|[TranslationAttachToTitleType](#TranslationAttachToTitleType)|

## <a name="NavigationPanelType"></a>[NavigationPanelType](Search.xml#L371)


Property|Type|Description
:-------|:---|:----------
[urlElement](Search.xml#L372)|String|
[displayPosition](Search.xml#L373)|Int32|
[label](Search.xml#L374)|String|

## <a name="TranslationAttachByPositionType"></a>[TranslationAttachByPositionType](Search.xml#L376)


Property|Type|Description
:-------|:---|:----------
[urlElement](Search.xml#L377)|String|
[responseFieldPosition](Search.xml#L378)|Int32|

## <a name="TranslationAttachToTitleType"></a>[TranslationAttachToTitleType](Search.xml#L380)


Property|Type|Description
:-------|:---|:----------
[urlElement](Search.xml#L381)|String|

## <a name="BoostingType"></a>[BoostingType](Search.xml#L385)


Property|Type|Description
:-------|:---|:----------
[definitions](Search.xml#L386)|\[[BoostingDefinitionsType](#BoostingDefinitionsType)\]|
[templates](Search.xml#L387)|\[[BoostingTemplatesType](#BoostingTemplatesType)\]|

## <a name="BoostingDefinitionsType"></a>[BoostingDefinitionsType](Search.xml#L389)


Property|Type|Description
:-------|:---|:----------
[id](Search.xml#L390)|String|
[precondition](Search.xml#L391)|String|
[definition](Search.xml#L392)|String|

## <a name="BoostingTemplatesType"></a>[BoostingTemplatesType](Search.xml#L394)


Property|Type|Description
:-------|:---|:----------
[id](Search.xml#L395)|String|
[template](Search.xml#L396)|String|
