# EnterpriseSearchHana Vocabulary
**Namespace: [com.sap.vocabularies.EnterpriseSearchHana.v1](EnterpriseSearchHana.xml)**

Terms for Enterprise Search Hana


## Terms

Term|Type|Description
:---|:---|:----------
[arbitraryCardinality](EnterpriseSearchHana.xml#L36)|Boolean|<a name="arbitraryCardinality"></a>Defines a column as a multi-value column.<br>This means that the column comes from an 1:n join and that it is returned in the search result as an array. This annotation is only allowed for columns that are of a SQL type that can be used in a group by clause.
[weight](EnterpriseSearchHana.xml#L41)|Decimal|<a name="weight"></a>Defines the ranking weight of a column that is used to calculate the overall score.<br>Only one of the annotations @EnterpriseSearchHana.weight and @Search.ranking can be used for a column.
[identifier](EnterpriseSearchHana.xml#L45)|String|<a name="identifier"></a>Defines the OData identifier of a column. The value has to be a valid OData identifier.<br>If an identifier is defined, the identifier is used instead of the original column name in all interfaces of esh_search() including the metadata call. In other words, the internal column name is not visible to the users of esh_search(). If this annotation is not given, the column name is used as an identifier.
[numc](EnterpriseSearchHana.xml#L49)|Boolean|<a name="numc"></a>Defines a column as an ABAP NUMC column (a numeric value padded with leading zeros).<br>Without score functions, a search in a NUMC column is done similar to an alphanum search limited to numeric characters.Interval facets are returned, if a facet is requested for a NUMC column.
[layoutStructuredObject](EnterpriseSearchHana.xml#L54)|[LayoutStructuredObjectType](#LayoutStructuredObjectType)|<a name="layoutStructuredObject"></a>Defines a subobject of the anchor object<br>This means that the columns of the subobject come from a 1:n join and are returned in the search result as an array.
[uiResource](EnterpriseSearchHana.xml#L94)|[UiResourceType](#UiResourceType)|<a name="uiResource"></a>
[translation](EnterpriseSearchHana.xml#L107)|\[[TranslationType](#TranslationType)\]|<a name="translation"></a>Defines multilingual UI text directly in the search configuration as an alternative to resource bundles. The texts are returned in the output of a metadata call.
[navigation](EnterpriseSearchHana.xml#L122)|[NavigationType](#NavigationType)|<a name="navigation"></a>
[boosting](EnterpriseSearchHana.xml#L141)|[BoostingType](#BoostingType)|<a name="boosting"></a>

## <a name="LayoutStructuredObjectType"></a>[LayoutStructuredObjectType](EnterpriseSearchHana.xml#L58)


Property|Type|Description
:-------|:---|:----------
[arbitraryCardinality](EnterpriseSearchHana.xml#L59)|Boolean|defines that the subobject comes from a 1:n join and that there may be multiple subobject instances for a given anchor object.
[layerId](EnterpriseSearchHana.xml#L63)|String|Defines the name of the subobject.
[childIds](EnterpriseSearchHana.xml#L66)|\[String\]|Defines the names of other subobjects that are included within the subobject.
[defaultExpand](EnterpriseSearchHana.xml#L69)|[DefaultExpandType](#DefaultExpandType)|defines which subobjects are returned in the search result.
[elementList](EnterpriseSearchHana.xml#L72)|\[[ElementListType](#ElementListType)\]|Defines the view columns that belong to the subobject.

## <a name="DefaultExpandType"></a>[DefaultExpandType](EnterpriseSearchHana.xml#L76)


Member|Value|Description
:-----|----:|:----------
[WHY_FOUND](EnterpriseSearchHana.xml#L77)|0|Only the subobject of the anchor object are returned that contain at least one of the search terms.
[ALL](EnterpriseSearchHana.xml#L80)|1|All subobjects of an anchor object are returned.

## <a name="ElementListType"></a>[ElementListType](EnterpriseSearchHana.xml#L84)


Property|Type|Description
:-------|:---|:----------
[element](EnterpriseSearchHana.xml#L85)|String|Contains the name of a view column that belongs to the subobject.
[key](EnterpriseSearchHana.xml#L88)|Boolean|Defines if a column is part of the subobject's key. Used to identify the distinct subobjects of an anchor object.<br>If there are no key columns defined for a subobject, all columns are used to identify the distinct subobjects.

## <a name="UiResourceType"></a>[UiResourceType](EnterpriseSearchHana.xml#L95)


Property|Type|Description
:-------|:---|:----------
[label](EnterpriseSearchHana.xml#L96)|[UiResourceLabelType](#UiResourceLabelType)|

## <a name="UiResourceLabelType"></a>[UiResourceLabelType](EnterpriseSearchHana.xml#L98)


Property|Type|Description
:-------|:---|:----------
[bundle](EnterpriseSearchHana.xml#L99)|Boolean|Defines the name of a resource bundle. Can be used by the search ui to load a view label.
[key](EnterpriseSearchHana.xml#L102)|String|defines the name of a key in a resource bundle. Can be used by the search ui to load a view label.

## <a name="TranslationType"></a>[TranslationType](EnterpriseSearchHana.xml#L110)
Placeholder that is later used in the search configuration to reference the translated texts.

Property|Type|Description
:-------|:---|:----------
[id](EnterpriseSearchHana.xml#L111)|String|
[value](EnterpriseSearchHana.xml#L113)|\[[TranslationValueType](#TranslationValueType)\]|

## <a name="TranslationValueType"></a>[TranslationValueType](EnterpriseSearchHana.xml#L115)


Property|Type|Description
:-------|:---|:----------
[language](EnterpriseSearchHana.xml#L116)|String|Language code with location, IE: en_GB, en_US, en_AU, de_DE, de_AT.
[text](EnterpriseSearchHana.xml#L119)|String|

## <a name="NavigationType"></a>[NavigationType](EnterpriseSearchHana.xml#L123)


Property|Type|Description
:-------|:---|:----------
[panel](EnterpriseSearchHana.xml#L124)|\[[NavigationPanelType](#NavigationPanelType)\]|
[attachByPosition](EnterpriseSearchHana.xml#L125)|\[[TranslationAttachByPositionType](#TranslationAttachByPositionType)\]|
[attachToTitle](EnterpriseSearchHana.xml#L126)|[TranslationAttachToTitleType](#TranslationAttachToTitleType)|

## <a name="NavigationPanelType"></a>[NavigationPanelType](EnterpriseSearchHana.xml#L128)


Property|Type|Description
:-------|:---|:----------
[urlElement](EnterpriseSearchHana.xml#L129)|String|
[displayPosition](EnterpriseSearchHana.xml#L130)|Int32|
[label](EnterpriseSearchHana.xml#L131)|String|

## <a name="TranslationAttachByPositionType"></a>[TranslationAttachByPositionType](EnterpriseSearchHana.xml#L133)


Property|Type|Description
:-------|:---|:----------
[urlElement](EnterpriseSearchHana.xml#L134)|String|
[responseFieldPosition](EnterpriseSearchHana.xml#L135)|Int32|

## <a name="TranslationAttachToTitleType"></a>[TranslationAttachToTitleType](EnterpriseSearchHana.xml#L137)


Property|Type|Description
:-------|:---|:----------
[urlElement](EnterpriseSearchHana.xml#L138)|String|

## <a name="BoostingType"></a>[BoostingType](EnterpriseSearchHana.xml#L142)


Property|Type|Description
:-------|:---|:----------
[definitions](EnterpriseSearchHana.xml#L143)|\[[BoostingDefinitionsType](#BoostingDefinitionsType)\]|
[templates](EnterpriseSearchHana.xml#L144)|\[[BoostingTemplatesType](#BoostingTemplatesType)\]|

## <a name="BoostingDefinitionsType"></a>[BoostingDefinitionsType](EnterpriseSearchHana.xml#L146)


Property|Type|Description
:-------|:---|:----------
[id](EnterpriseSearchHana.xml#L147)|String|
[precondition](EnterpriseSearchHana.xml#L148)|String|
[definition](EnterpriseSearchHana.xml#L149)|String|

## <a name="BoostingTemplatesType"></a>[BoostingTemplatesType](EnterpriseSearchHana.xml#L151)


Property|Type|Description
:-------|:---|:----------
[id](EnterpriseSearchHana.xml#L152)|String|
[template](EnterpriseSearchHana.xml#L153)|String|
