---
title: "4.16 Ignore query option"
description: ""
category: "4. OData features"
ms.date: 08/11/2015
---
# 4.16 Ignore query option

In OData WebApi 5.7, we can ignore some query options when calling `ODataQueryOption` `ApplyTo` method, this is helpful when your odata service is integrate with other service that may already applied those query options. 

### Customize 

```C#
public class MyEnableQueryAttribute : EnableQueryAttribute
{
    public override IQueryable ApplyQuery(IQueryable queryable, ODataQueryOptions queryOptions)
    {
       // Don't apply Skip and Top.
       var ignoreQueryOptions = AllowedQueryOptions.Skip | AllowedQueryOptions.Top;
       return queryOptions.ApplyTo(queryable, ignoreQueryOptions);
    }
}
```

### Controller

```C#
[MyEnableQuery]
public IHttpActionResult Get()
{
    return Ok(_products);
}
```

### Result
Then your queryOption won't apply Top and Skip. 