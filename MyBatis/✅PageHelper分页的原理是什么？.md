# ✅PageHelper分页的原理是什么？

# 典型回答


PageHelper是MyBatis中提供的分页插件，主要是用来做物理分页的。



当我们在代码中使用`PageHelper.startPage(int pageNum, int pageSize)`设置分页参数之后，其实PageHelper会把他们存储到ThreadLocal中。



PageHelper会在执行器的query方法执行之前，会从ThreadLocal中再获取分页参数信息，页码和页大小，然后执行分页算法，计算需要返回的数据块的起始位置和大小。最后，**PageHelper会通过修改SQL语句的方式，在SQL后面动态拼接上limit语句**，限定查询的数据范围，从而实现物理分页的效果。并且在查询结束后再清除ThreadLocal中的分页参数。





![1712156743499-671e4535-9c11-4ace-a926-2565e236f798.png](./img/SO4DIoyWxWniD4g0/1712156743499-671e4535-9c11-4ace-a926-2565e236f798-847330.webp)



> 更新: 2024-04-04 17:07:18  
> 原文: <https://www.yuque.com/hollis666/qfgwk3/ogng83zwfrqblu5e>