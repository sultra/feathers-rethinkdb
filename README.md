> 为正在开发的项目加上一些功能 @JKR3_TEAM

feathers-rethinkdb
==================

It's forked from https://github.com/feathersjs-ecosystem/feathers-rethinkdb



Installation
------------

```bash
npm install rethinkdbdash feathers-rethinkdb-R3 --save
```

Documentation
-------------

Please read [Official](https://docs.feathersjs.com)

我们增加的特性
-------------

1. 支持查询排序用二级索引 / support secend index  when use "order by" 

``` javascript
cosnt options={index:['index1','index2']}
```

2. Patch方法增强/ Upgrade Patch method

   1. params上增加两个可选属性，“getTransData” 、"reqlUpdate"，均为方法类型

   ``` javascript
   /**
   *在实际修改前将获得的数据修改成实际更新到内容
   **/
   params.getTransData=function(pre_data){
     //process
     return actual_update_data;
   }
   query.then(pre_data=>{
   	return query.update(params.getTransData(pre_data));
   });

   ```

   ``` javascript
   /**
   *在更新时添加或修改更新条件
   **/
   params.reqlUpdate=function(row){
     //process 
   }
   return query.update(row => {
     return params.reqlUpdate(row);
   })
   ```

3. watch 方法中增加对 changes()方法中传入参数的支持
``` js
  table.changes({
    squash:false,
    includeInitial:false,
    includeStates:false,
    includeOffsets:false,
    includeTypes:false
  })
```

License
-------
Licensed under the [MIT license](LICENSE).

Author
------
[SULTRA](https://github.com/sultra)
