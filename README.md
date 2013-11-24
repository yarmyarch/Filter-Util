Filter-Util
===========

### Descriptions

You'll know what's it if you've used the filters in wordpress :)

An simple MVC tool that could be used separating extra actions from some a complex logic.

If you want more controls to some a function by applying series of hooks, check the <a href="https://github.com/yarmyarch/Aop-in-js" target="_blank">AopUtil</a> instead.

Check index.html for a demo.

### Public functions

#### FilterUtil.addFilter
Add a filter for a specific identifier. 

```js
// usage
FilterUtil.addFilter(filterName, handler[, priority]);

// params
filterName : 
    {String} filter identifier.
handler : 
    /**
     * @param lastReturnedValue : Value returned by last filter attached to the identifier.
     * if this filter is first one that's executed, it should be original value.
     * @param argument1 : Argument list parsed by applyFilters, if exsit.
     */
    {Function(lastReturnedValue[, argument1[, argument2[, ...]]])}
        handler that receives params above.
[priority] : 
    {int} optional. Default is 10, any other values as you wish.
    Determines the order of handlers that would be executed,
    Lower numbers correspond with earlier execution.
```

#### FilterUtil.removeFilter
Try to remove a specific filter under the specific priority. If it's attached for multiple times, all of them would be removed.
    
```js
// usage
FilterUtil.removeFilter(filterName, handler[, priority]);

// params
filterName : 
    {String} filter identifier.
handler : 
    {Function(lastReturnedValue[, argument1[, argument2[, ...]]])} 
        the handler given in addFilter
[priority] : 
    {int} optional. Default is 10, any other values as you wish, 
    just make sure it's the same as it's added.
```

#### FilterUtil.applyFilters
Execute all attacheed filters. Do nothing if no filters attached.
    
```js
// usage
FilterUtil.applyFilters(filterName, originalValue[, argument1[, argument2[, ...]]]);

// params
filterName : 
    {String} filter identifier.
originalValue : 
    The original value that would be filtered.
[argument1] : 
    optional. Argument list that might be required by handlers.
```

#### FilterUtil.clearFilters
As you can see, good luck to you using it.
    
```js
// usage
FilterUtil.clearFilters(filterName);

// params
filterName : 
    {String} filter identifier.
```