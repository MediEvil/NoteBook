sql 笔记
聚集索引 辅助索引
增加聚集会重建表
增加辅助索引会加共享锁

辅助索引
最左匹配
右边索引不能用范围
回表
select * from table where xx_id = 123 limit 50000,50
用下面的
(select id from table where xx_id = 123 limit 50000,50) b on a.id = b.id 

窗口函数
row_number over (order by
row_number over (partition by
rank() over (order by